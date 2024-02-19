
#include <stdio.h>
#include <string.h>

void moveWords(char *str) {
    int len = strlen(str);
    char lastChar = str[len - 1];
    int lastCharIndex = len - 1;

    while (lastCharIndex >= 0 && str[lastCharIndex] != ' ' && str[lastCharIndex] != '\t') {
        lastCharIndex--;
    }

    while (lastCharIndex < len - 1) {
        int wordEnd = lastCharIndex + 1;
        while (wordEnd < len && str[wordEnd] != ' ' && str[wordEnd] != '\t') {
            wordEnd++;
        }

        memmove(str, str + lastCharIndex + 2, wordEnd - lastCharIndex - 1);
        str[wordEnd - 1] = ' ';
        lastCharIndex = wordEnd;
    }
}

int main() {
    char inputString[100];

    fgets(inputString, sizeof(inputString), stdin);

    size_t length = strlen(inputString);
    if (inputString[length - 1] == '\n') {
        inputString[length - 1] = '\0';
    }

    moveWords(inputString);

    printf("Результат: %s\n", inputString);

    return 0;
}
