using System;
using System.Collections.Generic;

namespace TaskManagerApp
{
    // تعريف فئة المهمة
    public class Task
    {
        public string Name { get; set; }
        public int Priority { get; set; }       // 1=منخفضة، 2=متوسطة، 3=عالية
        public DateTime DateAdded { get; set; }
        public bool IsUrgent { get; set; }      // للاستخدام الاختياري

        public Task(string name, int priority)
        {
            Name = name;
            Priority = priority;
            DateAdded = DateTime.Now;
            IsUrgent = false;
        }
    }

    class Program
    {
        // مصفوفة ثابتة لتخزين المهام النشطة
        static Task[] tasks = new Task[100];
        static int taskCount = 0;

        // قائمة مرتبطة للمهام المكتملة
        static LinkedList<Task> completedTasks = new LinkedList<Task>();

        // قائمة انتظار للمهام العاجلة (اختياري)
        static Queue<Task> urgentTasks = new Queue<Task>();

        // مكدس للتراجع عن العمليات (اختياري)
        static Stack<Action> undoStack = new Stack<Action>();

        static void Main(string[] args)
        {
            while (true)
            {
                Console.WriteLine("\nاختر عملية:");
                Console.WriteLine("1. إضافة مهمة");
                Console.WriteLine("2. عرض جميع المهام");
                Console.WriteLine("3. حذف مهمة");
                Console.WriteLine("4. فرز حسب الأولوية");
                Console.WriteLine("5. فرز حسب تاريخ الإضافة");
                Console.WriteLine("6. إكمال مهمة");
                Console.WriteLine("7. عرض المهام المكتملة");
                Console.WriteLine("0. خروج");
                Console.Write("اختيارك: ");

                var input = Console.ReadLine();
                switch (input)
                {
                    case "1": AddTask(); break;
                    case "2": ShowAllTasks(); break;
                    case "3": DeleteTask(); break;
                    case "4": SortByPriority(); break;
                    case "5": SortByDate(); break;
                    case "6": CompleteTask(); break;
                    case "7": ShowCompletedTasks(); break;
                    case "0": return;
                    default: Console.WriteLine("خيار غير صالح"); break;
                }
            }
        }

        // دوال الوظائف الأساسية (ستُنفيذ لاحقاً)
        static void AddTask() { /* TODO: إضافة مهمة */ }
        static void ShowAllTasks() { /* TODO: عرض المهام */ }
        static void DeleteTask() { /* TODO: حذف مهمة */ }
        static void SortByPriority() { /* TODO: bubble sort */ }
        static void SortByDate() { /* TODO: quick sort */ }
        static void CompleteTask() { /* TODO: نقل إلى completedTasks */ }
        static void ShowCompletedTasks() { /* TODO: عرض المكتملة */ }
    }
}
