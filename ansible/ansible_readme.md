1.  defaults/main.yml  - переменные по умолчанию для роли. 
2.  handlers/main.yml  - обработчики, которые могут быть вызваны из задач в папке  tasks . 
3.  tasks/main.yml  - задачи, которые будут выполнены в указанном порядке. 
4.  templates/main.yml  - шаблоны файлов. 


start cmd `ansible-playbook -i hosts.ini playbook.yml`