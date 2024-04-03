class Student:
    def __init__(self, name, marks):
        self.name = name
        self.marks = marks
        self.grade = self.calculate_grade()

    def calculate_grade(self):
        total_marks = sum(self.marks)
        percentage = (total_marks / (len(self.marks) * 100)) * 100
        if percentage >= 80:
            return 'A'
        elif percentage >= 60:
            return 'B'
        else:
            return 'Fail'

class Class:
    def __init__(self, students):
        self.students = students

    def check_results(self):
        for student in self.students:
            if student.grade == 'Fail':
                if student.marks.count(0) >= 2:
                    print(f"{student.name} needs to reattempt all subjects.")
                else:
                    print(f"{student.name} has failed.")

if __name__ == "__main__":
    subjects = [100, 75, 75, 50]
    students_data = [
        ("Student 1", [80, 70, 65, 45]),
        ("Student 2", [90, 80, 70, 60]),
        ("Student 3", [55, 40, 30, 20]),
        ("Student 4", [70, 60, 55, 50]),
        ("Student 5", [85, 75, 70, 65])
    ]

    students = [Student(name, marks) for name, marks in students_data]
    my_class = Class(students)
    my_class.check_results()
