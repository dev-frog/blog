---
layout: post
title: Practical Binary Analysis
description: >

---

## ANATOMY OF A BINARY

Example code:

```c
#include <stdio.h>

#define FORMAT_STRING "%s"
#define MESSAGE "Hello, World!\n"


int main() {
    printf(FORMAT_STRING, MESSAGE);
    return 0;
}

```

> PreProcessor for program

```bash
gcc -E -P lession-1.c 

typedef long unsigned int size_t;
typedef __builtin_va_list __gnuc_va_list;
typedef unsigned char __u_char;
typedef unsigned short int __u_short;
typedef unsigned int __u_int;
typedef unsigned long int __u_long;
typedef signed char __int8_t;
typedef unsigned char __uint8_t;
typedef signed short int __int16_t;
typedef unsigned short int __uint16_t;
typedef signed int __int32_t;
typedef unsigned int __uint32_t;
typedef signed long int __int64_t;
typedef unsigned long int __uint64_t;
typedef __int8_t __int_least8_t;
typedef __uint8_t __uint_least8_t;
typedef __int16_t __int_least16_t;
typedef __uint16_t __uint_least16_t;
typedef __int32_t __int_least32_t;
typedef __uint32_t __uint_least32_t;
typedef __int64_t __int_least64_t;
typedef __uint64_t __uint_least64_t;
typedef long int __quad_t;
typedef unsigned long int __u_quad_t;
typedef long int __intmax_t;
typedef unsigned long int __uintmax_t;
typedef unsigned long int __dev_t;
typedef unsigned int __uid_t;
typedef unsigned int __gid_t;
typedef unsigned long int __ino_t;
typedef unsigned long int __ino64_t;
typedef unsigned int __mode_t;
typedef unsigned long int __nlink_t;
typedef long int __off_t;
typedef long int __off64_t;
typedef int __pid_t;
typedef struct { int __val[2]; } __fsid_t;
typedef long int __clock_t;
typedef unsigned long int __rlim_t;
typedef unsigned long int __rlim64_t;
typedef unsigned int __id_t;
typedef long int __time_t;
typedef unsigned int __useconds_t;
typedef long int __suseconds_t;
typedef long int __suseconds64_t;
typedef int __daddr_t;
typedef int __key_t;
typedef int __clockid_t;
typedef void * __timer_t;
typedef long int __blksize_t;
typedef long int __blkcnt_t;
typedef long int __blkcnt64_t;
typedef unsigned long int __fsblkcnt_t;
typedef unsigned long int __fsblkcnt64_t;
typedef unsigned long int __fsfilcnt_t;
typedef unsigned long int __fsfilcnt64_t;
typedef long int __fsword_t;
typedef long int __ssize_t;
typedef long int __syscall_slong_t;
typedef unsigned long int __syscall_ulong_t;
typedef __off64_t __loff_t;
typedef char *__caddr_t;
typedef long int __intptr_t;
typedef unsigned int __socklen_t;
typedef int __sig_atomic_t;
typedef struct
{
  int __count;
  union
  {
    unsigned int __wch;
    char __wchb[4];
  } __value;
} __mbstate_t;
typedef struct _G_fpos_t
{
  __off_t __pos;
  __mbstate_t __state;
} __fpos_t;
typedef struct _G_fpos64_t
{
  __off64_t __pos;
  __mbstate_t __state;
} __fpos64_t;
struct _IO_FILE;
typedef struct _IO_FILE __FILE;
struct _IO_FILE;
typedef struct _IO_FILE FILE;
struct _IO_FILE;
struct _IO_marker;
struct _IO_codecvt;
struct _IO_wide_data;
typedef void _IO_lock_t;
struct _IO_FILE
{
  int _flags;
  char *_IO_read_ptr;
  char *_IO_read_end;
  char *_IO_read_base;
  char *_IO_write_base;
  char *_IO_write_ptr;
  char *_IO_write_end;
  char *_IO_buf_base;
  char *_IO_buf_end;
  char *_IO_save_base;
  char *_IO_backup_base;
  char *_IO_save_end;
  struct _IO_marker *_markers;
  struct _IO_FILE *_chain;
  int _fileno;
  int _flags2;
  __off_t _old_offset;
  unsigned short _cur_column;
  signed char _vtable_offset;
  char _shortbuf[1];
  _IO_lock_t *_lock;
  __off64_t _offset;
  struct _IO_codecvt *_codecvt;
  struct _IO_wide_data *_wide_data;
  struct _IO_FILE *_freeres_list;
  void *_freeres_buf;
  size_t __pad5;
  int _mode;
  char _unused2[15 * sizeof (int) - 4 * sizeof (void *) - sizeof (size_t)];
};
typedef __ssize_t cookie_read_function_t (void *__cookie, char *__buf,
                                          size_t __nbytes);
typedef __ssize_t cookie_write_function_t (void *__cookie, const char *__buf,
                                           size_t __nbytes);
typedef int cookie_seek_function_t (void *__cookie, __off64_t *__pos, int __w);
typedef int cookie_close_function_t (void *__cookie);
typedef struct _IO_cookie_io_functions_t
{
  cookie_read_function_t *read;
  cookie_write_function_t *write;
  cookie_seek_function_t *seek;
  cookie_close_function_t *close;
} cookie_io_functions_t;
typedef __gnuc_va_list va_list;
typedef __off_t off_t;
typedef __ssize_t ssize_t;
typedef __fpos_t fpos_t;
extern FILE *stdin;
extern FILE *stdout;
extern FILE *stderr;
extern int remove (const char *__filename) __attribute__ ((__nothrow__ , __leaf__));
extern int rename (const char *__old, const char *__new) __attribute__ ((__nothrow__ , __leaf__));
extern int renameat (int __oldfd, const char *__old, int __newfd,
       const char *__new) __attribute__ ((__nothrow__ , __leaf__));
extern int fclose (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern FILE *tmpfile (void)
  __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (fclose, 1))) ;
extern char *tmpnam (char[20]) __attribute__ ((__nothrow__ , __leaf__)) ;
extern char *tmpnam_r (char __s[20]) __attribute__ ((__nothrow__ , __leaf__)) ;
extern char *tempnam (const char *__dir, const char *__pfx)
   __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (__builtin_free, 1)));
extern int fflush (FILE *__stream);
extern int fflush_unlocked (FILE *__stream);
extern FILE *fopen (const char *__restrict __filename,
      const char *__restrict __modes)
  __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (fclose, 1))) ;
extern FILE *freopen (const char *__restrict __filename,
        const char *__restrict __modes,
        FILE *__restrict __stream) __attribute__ ((__nonnull__ (3)));
extern FILE *fdopen (int __fd, const char *__modes) __attribute__ ((__nothrow__ , __leaf__))
  __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (fclose, 1))) ;
extern FILE *fopencookie (void *__restrict __magic_cookie,
     const char *__restrict __modes,
     cookie_io_functions_t __io_funcs) __attribute__ ((__nothrow__ , __leaf__))
  __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (fclose, 1))) ;
extern FILE *fmemopen (void *__s, size_t __len, const char *__modes)
  __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (fclose, 1))) ;
extern FILE *open_memstream (char **__bufloc, size_t *__sizeloc) __attribute__ ((__nothrow__ , __leaf__))
  __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (fclose, 1))) ;
extern void setbuf (FILE *__restrict __stream, char *__restrict __buf) __attribute__ ((__nothrow__ , __leaf__))
  __attribute__ ((__nonnull__ (1)));
extern int setvbuf (FILE *__restrict __stream, char *__restrict __buf,
      int __modes, size_t __n) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern void setbuffer (FILE *__restrict __stream, char *__restrict __buf,
         size_t __size) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern void setlinebuf (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int fprintf (FILE *__restrict __stream,
      const char *__restrict __format, ...) __attribute__ ((__nonnull__ (1)));
extern int printf (const char *__restrict __format, ...);
extern int sprintf (char *__restrict __s,
      const char *__restrict __format, ...) __attribute__ ((__nothrow__));
extern int vfprintf (FILE *__restrict __s, const char *__restrict __format,
       __gnuc_va_list __arg) __attribute__ ((__nonnull__ (1)));
extern int vprintf (const char *__restrict __format, __gnuc_va_list __arg);
extern int vsprintf (char *__restrict __s, const char *__restrict __format,
       __gnuc_va_list __arg) __attribute__ ((__nothrow__));
extern int snprintf (char *__restrict __s, size_t __maxlen,
       const char *__restrict __format, ...)
     __attribute__ ((__nothrow__)) __attribute__ ((__format__ (__printf__, 3, 4)));
extern int vsnprintf (char *__restrict __s, size_t __maxlen,
        const char *__restrict __format, __gnuc_va_list __arg)
     __attribute__ ((__nothrow__)) __attribute__ ((__format__ (__printf__, 3, 0)));
extern int vasprintf (char **__restrict __ptr, const char *__restrict __f,
        __gnuc_va_list __arg)
     __attribute__ ((__nothrow__)) __attribute__ ((__format__ (__printf__, 2, 0))) ;
extern int __asprintf (char **__restrict __ptr,
         const char *__restrict __fmt, ...)
     __attribute__ ((__nothrow__)) __attribute__ ((__format__ (__printf__, 2, 3))) ;
extern int asprintf (char **__restrict __ptr,
       const char *__restrict __fmt, ...)
     __attribute__ ((__nothrow__)) __attribute__ ((__format__ (__printf__, 2, 3))) ;
extern int vdprintf (int __fd, const char *__restrict __fmt,
       __gnuc_va_list __arg)
     __attribute__ ((__format__ (__printf__, 2, 0)));
extern int dprintf (int __fd, const char *__restrict __fmt, ...)
     __attribute__ ((__format__ (__printf__, 2, 3)));
extern int fscanf (FILE *__restrict __stream,
     const char *__restrict __format, ...) __attribute__ ((__nonnull__ (1)));
extern int scanf (const char *__restrict __format, ...) ;
extern int sscanf (const char *__restrict __s,
     const char *__restrict __format, ...) __attribute__ ((__nothrow__ , __leaf__));
extern int fscanf (FILE *__restrict __stream, const char *__restrict __format, ...) __asm__ ("" "__isoc99_fscanf") __attribute__ ((__nonnull__ (1)));
extern int scanf (const char *__restrict __format, ...) __asm__ ("" "__isoc99_scanf") ;
extern int sscanf (const char *__restrict __s, const char *__restrict __format, ...) __asm__ ("" "__isoc99_sscanf") __attribute__ ((__nothrow__ , __leaf__));
extern int vfscanf (FILE *__restrict __s, const char *__restrict __format,
      __gnuc_va_list __arg)
     __attribute__ ((__format__ (__scanf__, 2, 0))) __attribute__ ((__nonnull__ (1)));
extern int vscanf (const char *__restrict __format, __gnuc_va_list __arg)
     __attribute__ ((__format__ (__scanf__, 1, 0))) ;
extern int vsscanf (const char *__restrict __s,
      const char *__restrict __format, __gnuc_va_list __arg)
     __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__format__ (__scanf__, 2, 0)));
extern int vfscanf (FILE *__restrict __s, const char *__restrict __format, __gnuc_va_list __arg) __asm__ ("" "__isoc99_vfscanf")
     __attribute__ ((__format__ (__scanf__, 2, 0))) __attribute__ ((__nonnull__ (1)));
extern int vscanf (const char *__restrict __format, __gnuc_va_list __arg) __asm__ ("" "__isoc99_vscanf")
     __attribute__ ((__format__ (__scanf__, 1, 0))) ;
extern int vsscanf (const char *__restrict __s, const char *__restrict __format, __gnuc_va_list __arg) __asm__ ("" "__isoc99_vsscanf") __attribute__ ((__nothrow__ , __leaf__))
     __attribute__ ((__format__ (__scanf__, 2, 0)));
extern int fgetc (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int getc (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int getchar (void);
extern int getc_unlocked (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int getchar_unlocked (void);
extern int fgetc_unlocked (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int fputc (int __c, FILE *__stream) __attribute__ ((__nonnull__ (2)));
extern int putc (int __c, FILE *__stream) __attribute__ ((__nonnull__ (2)));
extern int putchar (int __c);
extern int fputc_unlocked (int __c, FILE *__stream) __attribute__ ((__nonnull__ (2)));
extern int putc_unlocked (int __c, FILE *__stream) __attribute__ ((__nonnull__ (2)));
extern int putchar_unlocked (int __c);
extern int getw (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int putw (int __w, FILE *__stream) __attribute__ ((__nonnull__ (2)));
extern char *fgets (char *__restrict __s, int __n, FILE *__restrict __stream)
     __attribute__ ((__access__ (__write_only__, 1, 2))) __attribute__ ((__nonnull__ (3)));
extern __ssize_t __getdelim (char **__restrict __lineptr,
                             size_t *__restrict __n, int __delimiter,
                             FILE *__restrict __stream) __attribute__ ((__nonnull__ (4)));
extern __ssize_t getdelim (char **__restrict __lineptr,
                           size_t *__restrict __n, int __delimiter,
                           FILE *__restrict __stream) __attribute__ ((__nonnull__ (4)));
extern __ssize_t getline (char **__restrict __lineptr,
                          size_t *__restrict __n,
                          FILE *__restrict __stream) __attribute__ ((__nonnull__ (3)));
extern int fputs (const char *__restrict __s, FILE *__restrict __stream)
  __attribute__ ((__nonnull__ (2)));
extern int puts (const char *__s);
extern int ungetc (int __c, FILE *__stream) __attribute__ ((__nonnull__ (2)));
extern size_t fread (void *__restrict __ptr, size_t __size,
       size_t __n, FILE *__restrict __stream)
  __attribute__ ((__nonnull__ (4)));
extern size_t fwrite (const void *__restrict __ptr, size_t __size,
        size_t __n, FILE *__restrict __s) __attribute__ ((__nonnull__ (4)));
extern size_t fread_unlocked (void *__restrict __ptr, size_t __size,
         size_t __n, FILE *__restrict __stream)
  __attribute__ ((__nonnull__ (4)));
extern size_t fwrite_unlocked (const void *__restrict __ptr, size_t __size,
          size_t __n, FILE *__restrict __stream)
  __attribute__ ((__nonnull__ (4)));
extern int fseek (FILE *__stream, long int __off, int __whence)
  __attribute__ ((__nonnull__ (1)));
extern long int ftell (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern void rewind (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int fseeko (FILE *__stream, __off_t __off, int __whence)
  __attribute__ ((__nonnull__ (1)));
extern __off_t ftello (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern int fgetpos (FILE *__restrict __stream, fpos_t *__restrict __pos)
  __attribute__ ((__nonnull__ (1)));
extern int fsetpos (FILE *__stream, const fpos_t *__pos) __attribute__ ((__nonnull__ (1)));
extern void clearerr (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int feof (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int ferror (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern void clearerr_unlocked (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int feof_unlocked (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int ferror_unlocked (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern void perror (const char *__s) __attribute__ ((__cold__));
extern int fileno (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int fileno_unlocked (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int pclose (FILE *__stream) __attribute__ ((__nonnull__ (1)));
extern FILE *popen (const char *__command, const char *__modes)
  __attribute__ ((__malloc__)) __attribute__ ((__malloc__ (pclose, 1))) ;
extern char *ctermid (char *__s) __attribute__ ((__nothrow__ , __leaf__))
  __attribute__ ((__access__ (__write_only__, 1)));
extern void flockfile (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int ftrylockfile (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern void funlockfile (FILE *__stream) __attribute__ ((__nothrow__ , __leaf__)) __attribute__ ((__nonnull__ (1)));
extern int __uflow (FILE *);
extern int __overflow (FILE *, int);

int main() {
    printf("%s", "Hello, World!\n");
    return 0;
}

```

> Assembly generated by the compilation phase

```bash
gcc -S -masm=intel lession-1.c 

cat lession-1.s


        .file   "lession-1.c"
        .intel_syntax noprefix
        .text
        .section        .rodata
.LC0:
        .string "Hello, World!"
        .text
        .globl  main
        .type   main, @function
main:
.LFB0:
        .cfi_startproc
        push    rbp
        .cfi_def_cfa_offset 16
        .cfi_offset 6, -16
        mov     rbp, rsp
        .cfi_def_cfa_register 6
        lea     rax, .LC0[rip]
        mov     rdi, rax
        call    puts@PLT
        mov     eax, 0
        pop     rbp
        .cfi_def_cfa 7, 8
        ret
        .cfi_endproc
.LFE0:
        .size   main, .-main
        .ident  "GCC: (GNU) 13.2.1 20230801"
        .section        .note.GNU-stack,"",@progbits

```

> Generate a object file with gcc

```bash
gcc -c lession-1.c

file lession-1.o 
lession-1.o: ELF 64-bit LSB relocatable, x86-64, version 1 (SYSV), not stripped

```

> Get Symbols in the binary

```bash
readelf --syms a.out 

Symbol table '.dynsym' contains 7 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND _[...]@GLIBC_2.34 (2)
     2: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_deregisterT[...]
     3: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@GLIBC_2.2.5 (3)
     4: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
     5: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_registerTMC[...]
     6: 0000000000000000     0 FUNC    WEAK   DEFAULT  UND [...]@GLIBC_2.2.5 (3)

Symbol table '.symtab' contains 24 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS lession-1.c
     2: 0000000000000000     0 FILE    LOCAL  DEFAULT  ABS 
     3: 0000000000003de0     0 OBJECT  LOCAL  DEFAULT   21 _DYNAMIC
     4: 0000000000002014     0 NOTYPE  LOCAL  DEFAULT   17 __GNU_EH_FRAME_HDR
     5: 0000000000003fe8     0 OBJECT  LOCAL  DEFAULT   23 _GLOBAL_OFFSET_TABLE_
     6: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND __libc_start_mai[...]
     7: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_deregisterT[...]
     8: 0000000000004008     0 NOTYPE  WEAK   DEFAULT   24 data_start
     9: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@GLIBC_2.2.5
    10: 0000000000004018     0 NOTYPE  GLOBAL DEFAULT   24 _edata
    11: 0000000000001154     0 FUNC    GLOBAL HIDDEN    15 _fini
    12: 0000000000004008     0 NOTYPE  GLOBAL DEFAULT   24 __data_start
    13: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
    14: 0000000000004010     0 OBJECT  GLOBAL HIDDEN    24 __dso_handle
    15: 0000000000002000     4 OBJECT  GLOBAL DEFAULT   16 _IO_stdin_used
    16: 0000000000004020     0 NOTYPE  GLOBAL DEFAULT   25 _end
    17: 0000000000001040    38 FUNC    GLOBAL DEFAULT   14 _start
    18: 0000000000004018     0 NOTYPE  GLOBAL DEFAULT   25 __bss_start
    19: 0000000000001139    26 FUNC    GLOBAL DEFAULT   14 main
    20: 0000000000004018     0 OBJECT  GLOBAL HIDDEN    24 __TMC_END__
    21: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_registerTMC[...]
    22: 0000000000000000     0 FUNC    WEAK   DEFAULT  UND __cxa_finalize@G[...]
    23: 0000000000001000     0 FUNC    GLOBAL HIDDEN    12 _init

```

> Stripped an executable

```bash
strip --strip-all a.out 

file a.out 
a.out: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=399a77b57cb9e56064e4a7e1b21238ef17257223, for GNU/Linux 4.4.0, stripped


 readelf --syms a.out 

Symbol table '.dynsym' contains 7 entries:
   Num:    Value          Size Type    Bind   Vis      Ndx Name
     0: 0000000000000000     0 NOTYPE  LOCAL  DEFAULT  UND 
     1: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND _[...]@GLIBC_2.34 (2)
     2: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_deregisterT[...]
     3: 0000000000000000     0 FUNC    GLOBAL DEFAULT  UND puts@GLIBC_2.2.5 (3)
     4: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND __gmon_start__
     5: 0000000000000000     0 NOTYPE  WEAK   DEFAULT  UND _ITM_registerTMC[...]
     6: 0000000000000000     0 FUNC    WEAK   DEFAULT  UND [...]@GLIBC_2.2.5 (3)

```

> Disassembling an object file

```bash
objdump -sj .rodata lession-1.o 

lession-1.o:     file format elf64-x86-64

Contents of section .rodata:
 0000 48656c6c 6f2c2057 6f726c64 2100      Hello, World!.  

```

> Intel format

```bash
objdump -M intel -d lession-1.o 

lession-1.o:     file format elf64-x86-64


Disassembly of section .text:

0000000000000000 <main>:
   0:   55                      push   rbp
   1:   48 89 e5                mov    rbp,rsp
   4:   48 8d 05 00 00 00 00    lea    rax,[rip+0x0]        # b <main+0xb>
   b:   48 89 c7                mov    rdi,rax
   e:   e8 00 00 00 00          call   13 <main+0x13>
  13:   b8 00 00 00 00          mov    eax,0x0
  18:   5d                      pop    rbp
  19:   c3                      ret
code/frog/offensive-shellcode via C v13.2.1-gcc 🐍 v3.11.8 λ  
```

> Relocation symbols

```bash
readelf --relocs lession-1.o 

Relocation section '.rela.text' at offset 0x198 contains 2 entries:
  Offset          Info           Type           Sym. Value    Sym. Name + Addend
000000000007  000300000002 R_X86_64_PC32     0000000000000000 .rodata - 4
00000000000f  000500000004 R_X86_64_PLT32    0000000000000000 puts - 4

Relocation section '.rela.eh_frame' at offset 0x1c8 contains 1 entry:
  Offset          Info           Type           Sym. Value    Sym. Name + Addend
000000000020  000200000002 R_X86_64_PC32     0000000000000000 .text + 0

```

> Disassembling an exacutable

```bash
objdump -M intel -d a.out 

a.out:     file format elf64-x86-64


Disassembly of section .init:

0000000000001000 <.init>:
    1000:       f3 0f 1e fa             endbr64
    1004:       48 83 ec 08             sub    rsp,0x8
    1008:       48 8b 05 c1 2f 00 00    mov    rax,QWORD PTR [rip+0x2fc1]        # 3fd0 <puts@plt+0x2fa0>
    100f:       48 85 c0                test   rax,rax
    1012:       74 02                   je     1016 <puts@plt-0x1a>
    1014:       ff d0                   call   rax
    1016:       48 83 c4 08             add    rsp,0x8
    101a:       c3                      ret

Disassembly of section .plt:

0000000000001020 <puts@plt-0x10>:
    1020:       ff 35 ca 2f 00 00       push   QWORD PTR [rip+0x2fca]        # 3ff0 <puts@plt+0x2fc0>
    1026:       ff 25 cc 2f 00 00       jmp    QWORD PTR [rip+0x2fcc]        # 3ff8 <puts@plt+0x2fc8>
    102c:       0f 1f 40 00             nop    DWORD PTR [rax+0x0]

0000000000001030 <puts@plt>:
    1030:       ff 25 ca 2f 00 00       jmp    QWORD PTR [rip+0x2fca]        # 4000 <puts@plt+0x2fd0>
    1036:       68 00 00 00 00          push   0x0
    103b:       e9 e0 ff ff ff          jmp    1020 <puts@plt-0x10>

Disassembly of section .text:

0000000000001040 <.text>:
    1040:       f3 0f 1e fa             endbr64
    1044:       31 ed                   xor    ebp,ebp
    1046:       49 89 d1                mov    r9,rdx
    1049:       5e                      pop    rsi
    104a:       48 89 e2                mov    rdx,rsp
    104d:       48 83 e4 f0             and    rsp,0xfffffffffffffff0
    1051:       50                      push   rax
    1052:       54                      push   rsp
    1053:       45 31 c0                xor    r8d,r8d
    1056:       31 c9                   xor    ecx,ecx
    1058:       48 8d 3d da 00 00 00    lea    rdi,[rip+0xda]        # 1139 <puts@plt+0x109>
    105f:       ff 15 5b 2f 00 00       call   QWORD PTR [rip+0x2f5b]        # 3fc0 <puts@plt+0x2f90>
    1065:       f4                      hlt
    1066:       66 2e 0f 1f 84 00 00    cs nop WORD PTR [rax+rax*1+0x0]
    106d:       00 00 00 
    1070:       48 8d 3d a1 2f 00 00    lea    rdi,[rip+0x2fa1]        # 4018 <puts@plt+0x2fe8>
    1077:       48 8d 05 9a 2f 00 00    lea    rax,[rip+0x2f9a]        # 4018 <puts@plt+0x2fe8>
    107e:       48 39 f8                cmp    rax,rdi
    1081:       74 15                   je     1098 <puts@plt+0x68>
    1083:       48 8b 05 3e 2f 00 00    mov    rax,QWORD PTR [rip+0x2f3e]        # 3fc8 <puts@plt+0x2f98>
    108a:       48 85 c0                test   rax,rax
    108d:       74 09                   je     1098 <puts@plt+0x68>
    108f:       ff e0                   jmp    rax
    1091:       0f 1f 80 00 00 00 00    nop    DWORD PTR [rax+0x0]
    1098:       c3                      ret
    1099:       0f 1f 80 00 00 00 00    nop    DWORD PTR [rax+0x0]
    10a0:       48 8d 3d 71 2f 00 00    lea    rdi,[rip+0x2f71]        # 4018 <puts@plt+0x2fe8>
    10a7:       48 8d 35 6a 2f 00 00    lea    rsi,[rip+0x2f6a]        # 4018 <puts@plt+0x2fe8>
    10ae:       48 29 fe                sub    rsi,rdi
    10b1:       48 89 f0                mov    rax,rsi
    10b4:       48 c1 ee 3f             shr    rsi,0x3f
    10b8:       48 c1 f8 03             sar    rax,0x3
    10bc:       48 01 c6                add    rsi,rax
    10bf:       48 d1 fe                sar    rsi,1
    10c2:       74 14                   je     10d8 <puts@plt+0xa8>
    10c4:       48 8b 05 0d 2f 00 00    mov    rax,QWORD PTR [rip+0x2f0d]        # 3fd8 <puts@plt+0x2fa8>
    10cb:       48 85 c0                test   rax,rax
    10ce:       74 08                   je     10d8 <puts@plt+0xa8>
    10d0:       ff e0                   jmp    rax
    10d2:       66 0f 1f 44 00 00       nop    WORD PTR [rax+rax*1+0x0]
    10d8:       c3                      ret
    10d9:       0f 1f 80 00 00 00 00    nop    DWORD PTR [rax+0x0]
    10e0:       f3 0f 1e fa             endbr64
    10e4:       80 3d 2d 2f 00 00 00    cmp    BYTE PTR [rip+0x2f2d],0x0        # 4018 <puts@plt+0x2fe8>
    10eb:       75 33                   jne    1120 <puts@plt+0xf0>
    10ed:       55                      push   rbp
    10ee:       48 83 3d ea 2e 00 00    cmp    QWORD PTR [rip+0x2eea],0x0        # 3fe0 <puts@plt+0x2fb0>
    10f5:       00 
    10f6:       48 89 e5                mov    rbp,rsp
    10f9:       74 0d                   je     1108 <puts@plt+0xd8>
    10fb:       48 8b 3d 0e 2f 00 00    mov    rdi,QWORD PTR [rip+0x2f0e]        # 4010 <puts@plt+0x2fe0>
    1102:       ff 15 d8 2e 00 00       call   QWORD PTR [rip+0x2ed8]        # 3fe0 <puts@plt+0x2fb0>
    1108:       e8 63 ff ff ff          call   1070 <puts@plt+0x40>
    110d:       c6 05 04 2f 00 00 01    mov    BYTE PTR [rip+0x2f04],0x1        # 4018 <puts@plt+0x2fe8>
    1114:       5d                      pop    rbp
    1115:       c3                      ret
    1116:       66 2e 0f 1f 84 00 00    cs nop WORD PTR [rax+rax*1+0x0]
    111d:       00 00 00 
    1120:       c3                      ret
    1121:       66 66 2e 0f 1f 84 00    data16 cs nop WORD PTR [rax+rax*1+0x0]
    1128:       00 00 00 00 
    112c:       0f 1f 40 00             nop    DWORD PTR [rax+0x0]
    1130:       f3 0f 1e fa             endbr64
    1134:       e9 67 ff ff ff          jmp    10a0 <puts@plt+0x70>
    1139:       55                      push   rbp
    113a:       48 89 e5                mov    rbp,rsp
    113d:       48 8d 05 c0 0e 00 00    lea    rax,[rip+0xec0]        # 2004 <puts@plt+0xfd4>
    1144:       48 89 c7                mov    rdi,rax
    1147:       e8 e4 fe ff ff          call   1030 <puts@plt>
    114c:       b8 00 00 00 00          mov    eax,0x0
    1151:       5d                      pop    rbp
    1152:       c3                      ret

Disassembly of section .fini:

0000000000001154 <.fini>:
    1154:       f3 0f 1e fa             endbr64
    1158:       48 83 ec 08             sub    rsp,0x8
    115c:       48 83 c4 08             add    rsp,0x8
    1160:       c3                      ret
```

> Contents of the `.interp` sections

```bash
readelf -p .interp a.out 

String dump of section '.interp':
  [     0]  /lib64/ld-linux-x86-64.so.2

```
