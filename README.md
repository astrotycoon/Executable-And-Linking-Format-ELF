**ELF文件格式标准的中文翻译**

[System V Application Binary Interface](http://www.sco.com/developers/gabi/latest/contents.html)

[Oracle - ELF Application Binary Interface](https://docs.oracle.com/cd/E37838_01/html/E36783/glcfv.html#scrolltoc)

[链接程序和库指南](https://docs.oracle.com/cd/E26926_01/html/E25910/index.html)

[ELF and ABI Standards](https://refspecs.linuxbase.org/)

[ELF: From The Programmer's Perspective](http://beefchunk.com/documentation/sys-programming/binary_formats/elf/elf_from_the_programmers_perspective/elf.html)

[ELF Format Cheatsheet](https://gist.github.com/DtxdF/e6d940271e0efca7e0e2977723aec360)


if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi


PS1='${debian_chroot:+($debian_chroot)}\[\033[35;1m\][\t@\[\033[1;31m\]astrol:\w]\$ \[\033[0m\]'
