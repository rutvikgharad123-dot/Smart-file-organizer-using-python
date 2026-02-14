# Smart-file-organizer-using-python
import os 
import shutil
#folder path you want a organize
folder_path = os.getcwd() #current working directory

#file type discribe
file_types = {
    'Images': ['.jpg', '.jpeg', '.png', '.gif', '.bmp', '.tiff'],
    'Documents': ['.pdf', '.docx', '.txt', '.xlsx', '.pptx'],
    'Audio': ['.mp3', '.wav', '.aac', '.flac'], }
# Create folders if they don't exist
for folder in file_types.keys(): #Iterate through the keys of the file_types dictionary
    folder_dir = os.path.join(folder_path, folder)#Create the full path for the folder by joining the folder_path and the folder name
    if not os.path.exists(folder_dir):#Check if the folder already exists, if not, create it
        os.makedirs(folder_dir)#Move files to corresponding folders
        #organize files based on their extensions
for filename in os.listdir(folder_path):#Iterate through the files in the folder_path
    file_path = os.path.join(folder_path, filename)#Create the full path for the file by joining the folder_path and the filename
    if os.path.isfile(file_path):#Check if the path is a file (not a directory)
        file_extension = os.path.splitext(filename)[1].lower()#Get the file extension and convert it to lowercase
        for folder, extensions in file_types.items():#Iterate through the file_types dictionary
            if file_extension in extensions:#Check if the file extension matches any of the extensions in the current folder category
                shutil.move(file_path, os.path.join(folder_path, folder))#Move the file to the corresponding folder
                break
            #organize files
            for filename in os.listdir(folder_path):#Iterate through the files in the folder_path
                file_path = os.path.join(folder_path, filename)#Create the full path for the file by joining the folder_path and the filename
                if os.path.isfile(file_path):#Check if the path is a file (not a directory)
                    file_extension = os.path.splitext(filename)[1].lower()#Get the file extension and convert it to lowercase
                    for folder, extensions in file_types.items():#Iterate through the file_types dictionary
                        if file_extension in extensions:#Check if the file extension matches any of the extensions in the current folder category
                            shutil.move(file_path, os.path.join(folder_path, folder))#Move the file to the corresponding folder
                            break 
                        
                        #skip folders
                        if os.path.isdir(file_path):#Check if the path is a directory (not a file)
                            continue #Skip the directory and move to the next iteration of the loop   
                        #get file extension
                        file_extension = os.path.splitext(filename)[1].lower()#Get the file extension and convert it to lowercase
                        for folder, extensions in file_types.items():#Iterate through the file_types dictionary 
                            if file_extension in extensions:#Check if the file extension matches any of the extensions in the current folder category
                                shutil.move(file_path, os.path.join(folder_path, folder))#Move the file to the corresponding folder
                                break
                            
                            print("Files have been organized successfully!" ) # 
                        
