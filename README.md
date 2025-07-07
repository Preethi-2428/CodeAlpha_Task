# CodeAlpha_Task
import java.util.*;

class Student {
    String name;
    double grade;

    public Student(String name, double grade) {
        this.name = name;
        this.grade = grade;
    }
}

public class Main {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<Student> students = new ArrayList<>();

        System.out.print("Enter the number of students: ");
        int count = Integer.parseInt(scanner.nextLine());

        for (int i = 0; i < count; i++) {
            System.out.print("Enter student name: ");
            String name = scanner.nextLine();

            System.out.print("Enter " + name + "'s grade: ");
            double grade = Double.parseDouble(scanner.nextLine());

            students.add(new Student(name, grade));
        }

        double total = 0;
        double highest = Double.MIN_VALUE;
        double lowest = Double.MAX_VALUE;
        Student topStudent = null;
        Student bottomStudent = null;

        for (Student s : students) {
            total += s.grade;

            if (s.grade > highest) {
                highest = s.grade;
                topStudent = s;
            }

            if (s.grade < lowest) {
                lowest = s.grade;
                bottomStudent = s;
            }
        }

        double average = total / students.size();

        System.out.println("\n--- Grade Summary Report ---");
        for (Student s : students) {
            System.out.println(s.name + ": " + s.grade);
        }

        System.out.printf("Average Grade: %.2f%n", average);
        System.out.printf("Highest Grade: %.2f (%s)%n", highest, topStudent.name);
        System.out.printf("Lowest Grade: %.2f (%s)%n", lowest, bottomStudent.name);
    }
}
