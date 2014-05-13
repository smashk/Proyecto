Proyecto
========

Space Invaders
#include <ncurses.h>
#include <unistd.h>
void bordes() {
for(int i = 10 ; i < 40 ; i++){
mvprintw(i,20,"#");
}
for(int i = 10 ; i < 40 ; i++){
mvprintw(i,100,"#");
}
for(int i = 21 ; i < 100 ;i++){
mvprintw(10,i,"#");
}
for(int i = 21 ; i < 100 ;i++){
mvprintw(39,i,"#");
}
}
void nave(int y, int x){
mvprintw(y,x + 2,"|");
mvprintw(y + 1,x,"|");
mvprintw(y + 1,x + 1,"x");
mvprintw(y + 1,x + 2,"x");
mvprintw(y + 1, x + 3,"x");
mvprintw(y + 1,x + 4,"|");
}
int main(){
int esp = 4,y = 37,x = 30, ch;
initscr();
keypad(stdscr, TRUE);
curs_set(0);
noecho();
bordes();
while (1){
mvprintw(0,0,"Presione (Q) para finalizar");
nave(y,x);
ch = getch();
if(ch == 'q'){
endwin();
return 0;
}
if(x > 22){
if(ch == KEY_LEFT){
for(int i = 0 ; i < esp ; i++){
x;
nave(y,x);
bordes();
usleep(1000);
refresh();
clear();
}
}
}
if(x < 94){
if(ch == KEY_RIGHT){
for(int i = 0 ; i < esp ; i++){
x++;
nave(y,x);
bordes();
usleep(1000);
refresh();
clear();
}
}
}
if(ch == ' '){
for(int i = 36; i > 10 ;i){
mvprintw(i,x + 2,"|");
mvprintw(0,0,"Presione (Q) para finalizar");
nave(y,x);
bordes();
usleep(6000);
refresh();
clear();
}
}
bordes();
}
}
