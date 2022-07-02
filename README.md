# Make an ISO from kernel

In this I am going to make an iso from .bin with grub

<hr>

# Requirements

- grub-mkrescue

# resoures

- [https://intermezzos.github.io/book/first-edition/running-in-qemu.html](https://intermezzos.github.io/book/first-edition/running-in-qemu.html)

# Tutorial

```console
mkdir -p isofiles/boot/grub
```

grub.cfg file inside of `isofiles/boot/grub`

```console
set timeout=0
set default=0

menuentry "_word_of_os_" {
    multiboot2 /boot/_name_of_bin_.bin
    boot
}
```
the `_name_.bin` should be in `isofiles/boot/`

layout:

```
isofiles/
└── boot
    ├── grub
    │   └── grub.cfg
    └── kernel.bin
```


```console
grub-mkrescue -o _name_of_iso_.iso isofiles
```

then if you want you can run in qemu

```console
qemu-system-x86_64 -cdrom os.iso # or any other version of qemu
```
