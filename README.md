<pre> ```c 
#include <stdio.h>
#include <string.h>

#define MAX 100

struct Student {
    char id[10];
    char name[50];
    int age;
    float gpa;
};

int n = 0; // Số lượng sinh viên hiện tại
struct Student list[MAX];

// Thêm sinh viên mới
void addStudent() {
    printf("Nhập thông tin sinh viên %d:\n", n + 1);
    printf("Mã SV: ");
    scanf("%s", list[n].id);
    printf("Họ tên: ");
    scanf(" %[^\n]", list[n].name); // đọc cả dòng có dấu cách
    printf("Tuổi: ");
    scanf("%d", &list[n].age);
    printf("GPA: ");
    scanf("%f", &list[n].gpa);
    n++;
    printf("==> Đã thêm sinh viên thành công!\n");
}

// Hiển thị danh sách sinh viên
void showStudents() {
    printf("\n--- Danh sách sinh viên ---\n");
    for (int i = 0; i < n; i++) {
        printf("SV %d: %s | %s | Tuổi: %d | GPA: %.2f\n", i + 1, list[i].id, list[i].name, list[i].age, list[i].gpa);
    }
}

// Tìm kiếm sinh viên theo mã
void searchStudent() {
    char id[10];
    printf("Nhập mã SV cần tìm: ");
    scanf("%s", id);
    for (int i = 0; i < n; i++) {
        if (strcmp(list[i].id, id) == 0) {
            printf("Tìm thấy: %s | %s | Tuổi: %d | GPA: %.2f\n", list[i].id, list[i].name, list[i].age, list[i].gpa);
            return;
        }
    }
    printf("Không tìm thấy sinh viên.\n");
}

// Cập nhật sinh viên
void updateStudent() {
    char id[10];
    printf("Nhập mã SV cần cập nhật: ");
    scanf("%s", id);
    for (int i = 0; i < n; i++) {
        if (strcmp(list[i].id, id) == 0) {
            printf("Cập nhật tên mới: ");
            scanf(" %[^\n]", list[i].name);
            printf("Cập nhật tuổi: ");
            scanf("%d", &list[i].age);
            printf("Cập nhật GPA: ");
            scanf("%f", &list[i].gpa);
            printf("==> Cập nhật thành công!\n");
            return;
        }
    }
    printf("Không tìm thấy sinh viên để cập nhật.\n");
}

// Xóa sinh viên
void deleteStudent() {
    char id[10];
    printf("Nhập mã SV cần xóa: ");
    scanf("%s", id);
    for (int i = 0; i < n; i++) {
        if (strcmp(list[i].id, id) == 0) {
            for (int j = i; j < n - 1; j++) {
                list[j] = list[j + 1];
            }
            n--;
            printf("==> Đã xóa sinh viên.\n");
            return;
        }
    }
    printf("Không tìm thấy sinh viên để xóa.\n");
}

// Hàm main
int main() {
    int choice;
    do {
        printf("\n====== MENU ======\n");
        printf("1. Thêm sinh viên\n");
        printf("2. Hiển thị danh sách\n");
        printf("3. Tìm kiếm theo mã\n");
        printf("4. Cập nhật thông tin\n");
        printf("5. Xóa sinh viên\n");
        printf("0. Thoát\n");
        printf("Chọn: ");
        scanf("%d", &choice);
        switch (choice) {
            case 1: addStudent(); break;
            case 2: showStudents(); break;
            case 3: searchStudent(); break;
            case 4: updateStudent(); break;
            case 5: deleteStudent(); break;
            case 0: printf("Tạm biệt!\n"); break;
            default: printf("Lựa chọn không hợp lệ!\n");
        }
    } while (choice != 0);
    return 0;
}
      ``` </pre>
