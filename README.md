#!/bin/bash

file="students.txt"

while true
do
    echo "====== STUDENT RECORD MENU ======"
    echo "1. Add Student"
    echo "2. View All Students"
    echo "3. Search Student"
    echo "4. Delete Student"
    echo "5. Exit"
    echo -n "Enter your choice: "
    read choice

    case $choice in
        1)
            echo -n "Enter Roll No: "
            read roll
            echo -n "Enter Name: "
            read name
            echo -n "Enter Marks: "
            read marks

            echo "$roll | $name | $marks" >> $file
            echo "Student Added Successfully!"
            ;;

        2)
            echo "------ Student Records ------"
            if [ -f $file ]; then
                cat $file
            else
                echo "No records found!"
            fi
            ;;

        3)
            echo -n "Enter Roll No to search: "
            read roll
            grep "^$roll" $file
            ;;

        4)
            echo -n "Enter Roll No to delete: "
            read roll
            grep -v "^$roll" $file > temp.txt
            mv temp.txt $file
            echo "Record Deleted!"
            ;;

        5)
            echo "Exiting..."
            break
            ;;

        *)
            echo "Invalid choice!"
            ;;
    esac

    echo ""
done
