# app.fs

A set of function to handle file names and the file system.

# Path & File Name Manipulation

## app.fs.pathSeparator

```lua
local fn = "path" .. app.fs.pathSeparator .. "filename.png"
```

Return sthe preferred path separator of the current platform, it is
`/` on macOS and Linux, and `\` on Windows. Preferably you should use
[app.fs.joinPath()](#appfsjoinpath).

Example:

```lua
local sep = app.fs.pathSeparator
local fn = "path" .. sep .. "filename.png"
print(fn)
```

Will print `path/filename.png` on macOS or Linux, and `path\filename.png` on Windows.

## app.fs.filePath()

```lua
local pathPart = app.fs.filePath(fn)
```

Returns the path/directory part (as a string) of the given filename `fn`.

## app.fs.fileName()

```lua
local fileName = app.fs.fileName(fn)
```

Returns the file name (including the extension parth) of the given filename `fn`.

## app.fs.fileExtension()

```lua
local extension = app.fs.fileExtension(fn)
```

Returns the file extension (without including the `.`) of the given
filename `fn`. For example:

```lua
print(fs.fileExtension('path/file.png'))
```

Prints `png`.

## app.fs.fileTitle()

```lua
local title = app.fs.fileTitle(fn)
```

Returns the file title (without including the path nor the extension)
of the given filename `fn`. For example:

```lua
print(fs.fileExtension('path/file.png'))
```

Prints `file`.

## app.fs.filePathAndTitle()

```lua
local title = app.fs.filePathAndTitle(fn)
```

Returns the file path [joined](#appfsjoinpath) with the title (without
including the extension) of the given filename `fn`. For example:

```lua
print(fs.fileExtension('path/file.png'))
```

Prints `path/file`.

## app.fs.normalizePath()

## app.fs.joinPath()

```lua
local path = app.fs.joinPath(path1, path2)
```

# Special Folders

## app.currentPath

## app.appPath

## app.tempPath

## app.userDocsPath

## app.userConfigPath

# File System Access

## app.fs.isFile()

```lua
local exists = app.fs.is_file(fn)
```

Returns true if the given filename `fn` is a file.

## app.fs.isDirectory()

```lua
local exists = app.fs.is_directory(fn)
```

Returns true if the given filename `fn` is a directory.

## app.fs.fileSize()

```lua
local size = app.fs.fileSize(fn)
```

Returns the file size of the given filename `fn`.

## app.fs.listFiles()

```lua
local table = app.fs.listFiles(path)
```

Returns a list of files in the given directory `path`. The returned
value is a table where each element is a file name, each file name is
relative to the given `path`, they are not full path file names. In
case that you want to get a list of full file names you can do
something like this:

```lua
local dir = ...
for _,filename in pairs(app.fs.listFiles(dir)) do
  local fullFilename = app.fs.joinPath(dir, filename)
  ...
end
```