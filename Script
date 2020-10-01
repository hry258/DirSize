import os

def get_directory_size(directory):
    """Returns the `directory` size in bytes."""
    total = 0
    try:
        # print("[+] Getting the size of", directory)
        for entry in os.scandir(directory):
            if entry.is_file():
                # if it's a file, use stat() function
                total += entry.stat().st_size
            elif entry.is_dir():
                # if it's a directory, recursively call this function
                total += get_directory_size(entry.path)
    except NotADirectoryError:
        # if `directory` isn't a directory, get the file size then
        return os.path.getsize(directory)
    except PermissionError:
        # if for whatever reason we can't open the folder, return 0
        return 0
    return total

file = open(os.path.join(os.getcwd(), "dir_sizes.txt"), 'w+')

dir_path = "C:\\Program Files\\"

for dir in next(os.walk(dir_path))[1]:
    size = int(get_directory_size(os.path.join(dir_path, dir))) * 0.000001
    file.write(f"dir: {dir}\nsize: {size} MB\n\n")


