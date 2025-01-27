# scp
secure copy

```bash
scp [options] source_file user@host:destination_path
```

### Copying a file from local to remote:
```bash
scp /path/to/local/file.txt username@remote_host:/path/to/remote/directory/
```

### Copying a file from remote to local:
```bash
scp username@remote_host:/path/to/remote/file.txt /path/to/local/directory/
```

