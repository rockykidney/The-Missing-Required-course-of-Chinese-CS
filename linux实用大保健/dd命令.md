### 常见使用场景及示例

#### 1. 复制文件

将一个文件复制到另一个文件，示例命令如下：

收起



bash

```bash
dd if=source_file of=target_file
```

- `source_file` 是源文件的路径。
- `target_file` 是目标文件的路径。

例如，将 `file1.txt` 复制为 `file2.txt`：

收起



bash

```bash
dd if=file1.txt of=file2.txt
```

#### 2. 制作可引导的 USB 启动盘

将 ISO 镜像文件写入 USB 设备，需要注意的是，此操作会完全覆盖 USB 设备上的所有数据，因此在操作前请备份重要数据。

收起



bash

```bash
sudo dd if=image.iso of=/dev/sdX bs=4M status=progress
```

- `image.iso` 是 ISO 镜像文件的路径。
- `/dev/sdX` 是 USB 设备的设备名，可通过 `lsblk` 命令查看，X 是具体的设备标识，如 `sdb`、`sdc` 等。
- `bs=4M` 表示每次读写 4MB 的数据，可提高写入速度。
- `status=progress` 会显示复制的进度。

#### 3. 清空磁盘

使用 `dd` 命令将全零数据写入磁盘，从而清空磁盘数据，此操作同样会永久删除磁盘上的所有数据，请谨慎操作。

收起



bash









```bash
sudo dd if=/dev/zero of=/dev/sdX bs=4M count=1000
```

- `/dev/zero` 是一个特殊的设备文件，它会不断输出零值字节。
- `/dev/sdX` 是要清空的磁盘设备名。
- `count=1000` 表示只写入 1000 个块的数据。

#### 4. 测试磁盘读写速度

通过 `dd` 命令向磁盘写入大量数据来测试磁盘的写入速度：

收起



bash









```bash
dd if=/dev/zero of=testfile bs=1M count=1000 conv=fdatasync
```

- `testfile` 是用于测试的临时文件。
- `conv=fdatasync` 表示在写入完成后将数据同步到磁盘，确保测量的是实际的写入时间。

读取速度测试：

收起



bash









```bash
dd if=testfile of=/dev/null bs=1M
```

将 `testfile` 中的数据读取到 `/dev/null`（一个特殊的设备文件，会丢弃所有写入的数据），以此来测试磁盘的读取速度。

### 注意事项

- **谨慎操作**：`dd` 命令可以直接操作磁盘设备，若使用不当可能会导致数据丢失或系统损坏。在对磁盘设备进行操作前，请务必确认设备名和操作内容。
- **权限问题**：对磁盘设备进行操作通常需要 root 权限，因此在命令前加上 `sudo`。



分享



制作可引导的USB启动盘时，如果目标设备已经有数据，应该如何避免数据被覆盖？

如何使用dd命令将一个文件分割成指定大小的块？

在使用dd命令时，如何查看命令执行的进度？