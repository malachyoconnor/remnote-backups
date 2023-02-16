1. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/5x-kpFtSmurzNUmXPlR8GMTKt44S-pGI_uXQn-loC5FTlBbwH2KnTOZb_8vHNtz5Vc-B7ENcAojGyI83lmpHfPa1uVKKFQiiso5afgZZSAndShPRGx_1n1jctwLtBL13.png) 
    - 'a' is a char while "a" forms a string literal - e.g. an array of chars terminated with a null terminator \0.
2. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Y7TUSDPht8rMMmjwyibGk-4zzDDtqFry6U0sB0wSGHN80olxqx8IhSL4w7q1B7AwdfL5s1F1G8LzJ8q7-K3oTPmuVAZMovFSPG6aKrPGL5mZ2dLldl2lZEglvvYQf7oj.png) 
    - Yes, it will terminate when j equals 5 (e.g. the 5th ASCII character) as long as the two chars were initialized to 0 (which is not guaranteed). This is because you can store integer values in chars, ranging from -128 to 127 for unsigned chars.
3. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/dpZ64aPO1RH5e4EsS1UpUmsF6S1j8sYlwLx6vDShfHV1sW0kweO6ow9QUln0VP0NK6dzaTv2HQGT_siYVBxZQugXD5dBNPaOHMVYXAvK5T_8rvmGEmV0otOOn9oYFKxz.png)
    - ```c
#define SWAP(t,x,y) {\
    t temp = x;\
    x = y;\
    y = temp;\
}
```
4. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/wnEQh3sjj-ggBtFu8O9dNmiI2bL6F-ycmM394KL46Q4W-zJ1YH1L8zb5AuhRQgO0yH7tmlkZoS4jhEaKhz0CZSQcIHphGvCgeGCD5LGCuKrC4Cx7S9oxORSzpGNZE18s.png) 
    - No, the i++ will be evaluated twice - meaning the x in the second line of the macro will differ from the x in the third line of the macro (unless the values of v[i+1] and v[i+2] are the same). Similarly, if f(x) changes when it's called twice we will be getting different indices of w.
5. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/29dC0HQ66WGsn2vo69u4gNIJZt9N4FnfT5RwFJfM_G3BW7d5EhdsZOHsXWNjWacNu5zL96DZhIyb0C6NbtTEcqJ-TlSKnzxtwO9zn0fVU-ErJJFrKkkTJH3OY9HJb7no.png) 
    - ```c
#define SWAP(t,x,y) {\
    x = x - y;\
    y = y + x;\
    x = -x + y;\
}
``` 
6. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/VjH7bsEoeEXOb-ZAO4st3yXVKrJqqTgta_w8kMyod9Oe22Y2SY3BN4_UwFKmCzzzfdD_XCnzJG4-JQsuy9qVOjbjp3QFCvNPX9JwYgL0iIb2bJSPIhuJLUjEDjsW6djw.png)
    - p[-2] means the value two items before the pointer, this is legal if p is a pointer inside an array - this works because arrays allocate a contiguous block of memory which we can simply step along (pointer-wise) to reach earlier array-items.
7. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/6xCzQuVGM16QjzvbI4VY4CytzsorrFvjZX1148C4R1ovPU0H4YfSVTLPf1cagxhM-sD31wpTXg6cKaq74aQ609n_mIrRaPIb0Yvmv8tjBgN0IUPrbDjxPksgy8rh1VM-.png)  
    - ```c
char *strfind(const char *to_find, const char *to_search) {

    for (int i=0; i <= strlen(to_search) - strlen(to_find); i++ ) {
        int bookmark = 0;
        while (to_search[i+bookmark] == to_find[bookmark]) {
            if (bookmark == strlen(to_find)-1) {
                return to_search[i];
            }
            bookmark++;
        }
    }

    return NULL;
}
``` 
8. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/GtHkEKbpOG6jIjweOng_l6W05H7Yu9StIWUwwxs9dLB2QzAVtBTakVMQh-pHkARbLFo5t3z56QsppajKkhummkk_929JjfaKqROSQEgcZnq0Z_E6z2HzmF_wMr1mqUGD.png) 
    - A const pointer to an int is a pointer that cannot be changed, e.g. it will always point to that integer. However, the integer value itself can be changed. A pointer to a const int means the pointer can be changed to point at something else but the integer value cannot be changed. For a const pointer to a const int, neither the pointer nor the integer value can change.
9. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/ux0pai4I1dl1vDxBhD-cTy9Pz5Ne3eDRwJRRZ6_oW7PPjGjn5gxRXK5Yci7-xFVq4OFPnbgim5O5YHtj-Atp0MF37r5LXuplWnJQLl4xKYwVvp2RaesqucxNl1jgu8zW.png)
    - You could pass the values as const:
    - ```c
int adds_wont_change(const int *x, const int *y) {
    return *x+*y;
}
``` However, this is only an indication not a promise - the function still has it within its power to alter the arguments using casts.
10. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/q7tzntYJoJxSzhSjxKKL5xo7tQqMM2aUb8ggmcPB4hgSru1O59WOwTIIP62lL9UZ0YPkGiR0WsTifUx0OSi5me7cNjbveENoAqi5HehC-Vkt1tGajaBGdTSkVhekzIGE.png)
    - ```c
char* read_a_file(char input_filename[]) {
    FILE *file;
    file = fopen(input_filename, "r");
    char *string = malloc(1001);
    int memory_len = 1000;
    int currently_used = 0;
    if (file) {

        char c;
        while ((c = getc(file)) != EOF) {
            if (currently_used >= memory_len) {
                memory_len += 1000;
                string = realloc(string, memory_len);
            }
            string[currently_used] = c;
            currently_used++;
        }
        string[currently_used] = '\0';

    }

    fclose(file);
    return string;
}
``` 
11. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/0P3QCnLO7m_QReMJWnZiOuxdyR3x8rUtd4bSxrgQch_t8UEhDy3_iGE_cLCbN7043bbQXt9NcOorpBdzmfdQnEzNhkW0RsMTM0Ltx9cSEdIhb1jvO9vaDtXgTKXoCGka.png)
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/gcBE6wQaCcIKAs4I7o-7BUREOglWeWiNw8BVM06fB5iiiNPfsSRYKNJn0vki2qk-RDt2nyizBGi96ckZmwg_rQFMd10Tci3VUG2wwnunH84ZH-_MHy6VY6QWxUhE4njR.png)
    - Func1 can pass the pointer to the array to bar as the array still exists while bar runs, however when Func1 attempts to return the pointer to the array it's memory on the stack will be deallocated and thus any local variables will be lost and the values the pointer points to will be undefined - that is it's very possible they will be overwritten.
12. ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/KmKDW7D5NUYnv6HW7bY0Ut9L2F_PSp9sxF8ykkzky4_dUrWqcETQTVvt38Ziv905iqB3iSvV7SQEiPUOhrVvgJ79DOcg_jc1y26c4jvSACgavfpB3Sdz3ZP4AHY3UU-C.png)
    - Declaration simply tells the compiler a variable with the given name is going to be defined at some point, while definition allocates an area of memory for the variable. 
13. 
    - a.) ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/BlbZtBHf-NMCqx0Ni45FvW9jsJN0z5SnOn0pjG_FusfpndxTwr2s-jl7bfzlokLtRs-Q0rR3NqUjvoXWEm5YZkOonm8F1twD90e2am_nDGl_2sn6oatalYCCy3Zahj_l.png) 
    - **i is the integer value 78 0c 00 00 - which is  c78 which is 8 + 7*16 + 12 * 256 = 3192
    - p⇒c[2] is 62 in hex = 6*16 + 2 - slightly confused by this one, how does the compiler know to move 2 bytes along (as if its working with a char) rather than 9 bytes along (as if it was working with a struct i2c)
    - &(*pps)[1] is 0x18 + 2 = 16+8+2 = 26 (we move 2 forwards because we're dealingiwth a short)
    - ++p⇒i is 3192 + 1 = 3193 
    - 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/01AJtT87kPJuaTX5C5XZt2fkDMlszM_KcOj76VYkPP3spld9TxWz8igbTte2mVcT__CsI1CFlFlr5dQEdpgf-iLHbBo6NlIEVf1o_opvopjYa6F9XEK7M8kOF47i33A5.png)
        - First we cast our manager pointer to an employee pointer, however when we call wage(e) it sill uses the wage calculating function wage_man as the address not wage_em (we never changed the function being pointed to in the cast) - this then casts our pointer back to a manager pointer and calculates 40*10 + 20 = 420.
14. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/8zVLbpTXRupf0NULVKpgctjp9VkjS4ZcHNDQLuTRUyCGgd-edbhLPclwFXnuh2uXkjhKEDkIJdy5lWAaQEGJWZsfd_psK0fXIA_-BxK-hqwe3y9Ljza6RhcTgKYN287h.png)
        - ```c
#define CONCAT(a, b) (a b)
```
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/tic3LFyhReYVg9QlQVNVKS7tIwEUZBzjUdDYyiQSwuZ9_n2oEAijrte48htdQ-JcRmPa7VhPCys-1hnYCqOysIGcx4ATPZnLFITqbksPDrIto3T51OM49qsvJWNfTpJj.png)
        - Line 3 would not work, as CONCAT only works by leveraging the fact that string literals next to each other get concatenated in c - e.g. "a" "b" ⇒ "ab". All CONCAT does is paste the values next to each other and let the language do the rest - however CONCAT(b, a) will result in CONCAT("UoCCL", a) and the compiler cannot simply infer the value of a to combine the strings (not a string literal). 
        - Line 4 would not work, as j is not a pointer and you are thus taking the integer value of the pointer that concat(a,b) returns. 
        - concat(a,b) allocates memory on the heap and creates a list of chars, while CONCAT simply places two string literals next to each other (uses stack memory). concat(a,b) returns a pointer to the char array while CONCAT(a,b) will evaluate to the combined string literals. 
15. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Yc7pDYou5sDFsk8G-vXRMbYZJZkvIvoPnxYzVJzVgAFYuEB1gHaD_VDxY8yvyAernjZfJxRStzCKWnlxhKLebEBiAt38UsEs5HBe0iDRIrJeeAJE7wnMXcHI_ZDczi3L.png)
        - 500 bytes: (4 + 1 bytes) * 100. sizeof(struct Elem) =  5 bytes. long is 32 bits - compiler supports unaligned access, unlike all below.
        - 800 bytes: 32 bit machine, the long is 4 bytes, char is 1 byte. sizeof(struct Elem) =  8 bytes - but as 32 bit machine have to use two 4 byte words. Resulting in 100 * (4 + 4) = 800. 
        - 1200 bytes:  ^^48 bit machine, the long is 6 bytes, char is 1 byte, sizeof(struct Elem) =  12 bytes - but as 48 bit machine have to use two 4 byte words. Resulting in 100 * (6 + 6) = 1200. ^^ - possible answer but more likely: long 64 bits but aligned to 32 bits - 4+4+4 = 12
        - 1600 bytes: 64 bit machine, the long is 8 bytes, char is 1 byte sizeof(struct Elem) =  16 bytes- but as 64 bit machine have to use two 8 byte words. Resulting in 100 * (8 + 8) = 1600. 
    - ![](local:///home/mali/remnote/remnote-614c8a3b6997e6001643dfce/files/Ep4ntJAbb4n94rCUys5-sCXlO1A_qHTJLLNhp1VaSOwwGa6LU1mKBgnyYGPDlAocg7j39QT7M7vUoPh_zTSCQKRoMdoaB5ne8E74h4aC1Mc6_P7-HdZsak0E_be6VYwQ.png) 
        - The fundamental changed is converting the file that was created by a compiler using unaligned access to one that does not support unaligned access (no need for the added complexity when memory so abundant).  Also assumed little-endian.
        - ```c
struct Elem { signed long val; char flags; } v[NITEMS];
char temp[5*NITEMS]; // Each byte in the 5 byte line is going to become it's own item
fread(file, 1, size_of(temp), temp); // First we read the file and get every byte as a char value in our temp array
for (int i; i<size_of(result); i++) {
	
	v[i].val = temp[5*i] | temp[5*i+1]<<8 | temp[5*i+2]<<16 | temp[5*i+3]<<24; // This line combines them using bitwise ors - consider 00001010 | 1010000, combines the values as the zeroes are ignored
	v[i].flags = temp[5*i+4]; // last value is an actual char as we want it
}

``` We could simply have a flag to compute this for or not depending on if we're using this outdated format or not.
- 
