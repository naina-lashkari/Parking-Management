# Parking-Management

#include<stdio.h>
#include<conio.h>
#include<windows.h>
#include<string.h>
#include<stdlib.h>
#include<time.h>
struct car_vehicle
{
  long long int car_seconds;
  char car_owner_name[30];
  long long int car_owner_mobile_number;
  char time_of_arrival[30];
  char car_number[12];
};
struct truck_vehicle
{
  long long int truck_seconds;
  char truck_owner_name[30];
  long long int truck_owner_mobile_number;
  char time_of_arrival[30];
  char truck_number[12];
};
struct bike_vehicle
{
  long long int bike_seconds;
  char bike_owner_name[30];
  long long int bike_owner_mobile_number;
  char time_of_arrival[30];
  char bike_number[12];
};
struct bus_vehicle
{   
    long long int bus_seconds; 
  char bus_owner_name[30];
  long long int bus_owner_mobile_number;
  char time_of_arrival[30];
  char bus_number[12];
};
int main()
{
  int i=10;
  int count=0;
char owner_name[30];
long long int owner_mobile_number;
char vehicle_name[i];
char vehicle_number[i];
int vehicle_name_length;
char date_string[20];
int total_space , car_space ,truck_space , bike_space , bus_space , car_cost , truck_cost , bike_cost , bus_cost ;
int information_of_space_cost[9] ;
char car[]="car",truck[]="truck",bike[]="bike",bus[]="bus";
FILE *space_cost_information;
  int car_max_space,truck_max_space,bike_max_space,bus_max_space;
space_cost_information=fopen("space_cost_of_vehicles.txt","rb");
fclose(space_cost_information);
enter_again:
printf("enter the total number of space in parking stand:");
scanf("%d",&total_space);
information_of_space_cost[0]=total_space;
printf("\nenter the total number of space for car in parking stand:");
scanf("%d",&car_space);
printf("cost for parking car at stand for one day is:");
scanf("%d",&car_cost);
information_of_space_cost[1]=car_space;
information_of_space_cost[2]=car_cost;
printf("\nenter the total number of space for truck in parking stand:");
scanf("%d",&truck_space);
printf("cost for parking truck at stand for one day is:");
scanf("%d",&truck_cost);
information_of_space_cost[3]=truck_space;
information_of_space_cost[4]=truck_cost;
printf("\nenter the total number of space for bike in parking stand:");
scanf("%d",&bike_space);
printf("cost for parking bike at stand for one day is:");
scanf("%d",&bike_cost);
information_of_space_cost[5]=bike_space;
information_of_space_cost[6]=bike_cost;
printf("\nenter the total number of space for bus in parking stand:");
scanf("%d",&bus_space);
printf("cost for parking bus at stand for one day is:");
scanf("%d",&bus_cost);
information_of_space_cost[7]=bus_space;
information_of_space_cost[8]=bus_cost;
if(car_space+truck_space+bike_space+bus_space!=total_space)
{
  system("cls");
  printf("please fill information carefully\n\n");
  time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
  goto enter_again;
}
long int days;
  struct car_vehicle CAR[car_space];
  struct truck_vehicle TRUCK[truck_space];
  struct bike_vehicle BIKE[bike_space];
  struct bus_vehicle BUS[bus_space];
fclose(space_cost_information);
space_cost_information=fopen("space_cost_of_vehicles","w");
fwrite(information_of_space_cost,sizeof(int),9,space_cost_information);
fclose(space_cost_information);
char name[30]="www";
int g=12;
char vehicle_no[12]="www";
long long int sec=0;
int h=0;
FILE *car_information;
car_information=fopen("car_park_details","w");
for(car_space=0;car_space<information_of_space_cost[1];car_space++)
{
    CAR[car_space].car_owner_mobile_number=0;
    CAR[car_space].car_seconds=0;
for(g=0;g<12;g++)
  {
  CAR[car_space].car_number[g]=vehicle_no[g];
  }
  for(h=0;h<30;h++)
  {
    CAR[car_space].car_owner_name[h]=name[h];
  }
}
fwrite(CAR,sizeof(struct car_vehicle),information_of_space_cost[1],car_information);
fclose(car_information);
FILE *truck_information;
truck_information=fopen("truck_park_details","w");
for(truck_space=0;truck_space<information_of_space_cost[3];truck_space++)
{
    TRUCK[truck_space].truck_owner_mobile_number=0;
    TRUCK[truck_space].truck_seconds=0;
for(g=0;g<12;g++)
  {
  TRUCK[truck_space].truck_number[g]=vehicle_no[g];
  }
  for(h=0;h<30;h++)
  {
    TRUCK[truck_space].truck_owner_name[h]=name[h];
  }
}
fwrite(TRUCK,sizeof(struct truck_vehicle),information_of_space_cost[3],truck_information);
fclose(truck_information);
FILE *bike_information;
bike_information=fopen("bike_park_details","w");
for(bike_space=0;bike_space<information_of_space_cost[5];bike_space++)
{
    BIKE[bike_space].bike_owner_mobile_number=0;
    BIKE[bike_space].bike_seconds=0;
for(g=0;g<12;g++)
  {
  BIKE[bike_space].bike_number[g]=vehicle_no[g];
  }
  for(h=0;h<30;h++)
  {
    BIKE[bike_space].bike_owner_name[h]=name[h];
  }
}
fwrite(BIKE,sizeof(struct bike_vehicle),information_of_space_cost[5],bike_information);
fclose(bike_information);
FILE *bus_information;
bus_information=fopen("bus_park_details","w");
for(bus_space=0;bus_space<information_of_space_cost[7];bus_space++)
{
    BUS[bus_space].bus_owner_mobile_number=0;
    BUS[bus_space].bus_seconds=0;
for(g=0;g<12;g++)
  {
  BUS[bus_space].bus_number[g]=vehicle_no[g];
  }
  for(h=0;h<30;h++)
  {
    BUS[bus_space].bus_owner_name[h]=name[h];
  }
}
fwrite(BUS,sizeof(struct bus_vehicle),information_of_space_cost[7],bus_information);
fclose(bus_information);
while(1<2)
{
  space_cost_information=fopen("space_cost_of_vehicles","rb");
  fread(information_of_space_cost,sizeof(int),9,space_cost_information);
  fclose(space_cost_information);
  printf("\n");
  enter_name_carefully:
printf("enter the name of vehicle owner: ");
scanf("\n");
gets(owner_name);
int owner_name_length=strlen(owner_name);
if(owner_name_length<3)
{
  goto enter_name_carefully;
}
for(owner_name_length=0;owner_name[owner_name_length]!='\0';owner_name_length++)
{
  if(((owner_name[owner_name_length]>-1)&&(owner_name[owner_name_length]<32))((owner_name[owner_name_length]>33)&&(owner_name[owner_name_length]<65))((owner_name[owner_name_length]>90)&&(owner_name[owner_name_length]<97))((owner_name[owner_name_length]>122)&&(owner_name[owner_name_length]<128)))
{
  goto enter_name_carefully;
}
else if((owner_name[owner_name_length]==32)&&(owner_name[owner_name_length+1]==32))
{
goto enter_name_carefully;  
}
}
for(owner_name_length=0;owner_name[owner_name_length]!='\0';owner_name_length++)
{
  if((owner_name[owner_name_length]>96)&&(owner_name[owner_name_length]<123))
  {
  owner_name[owner_name_length]=owner_name[owner_name_length]-32;
  }
  else
  {
  owner_name[owner_name_length]=owner_name[owner_name_length]  ;
  }
}
printf("enter vehicle name:");
scanf("\n");
gets(vehicle_name);
vehicle_name_length=strlen(vehicle_name);
for(vehicle_name_length=0;vehicle_name[vehicle_name_length]!='\0';vehicle_name_length++)
{
  if(vehicle_name[vehicle_name_length]>64&&vehicle_name[vehicle_name_length]<91)
  {
    vehicle_name[vehicle_name_length]=vehicle_name[vehicle_name_length]+32;
  }
  else if(vehicle_name[vehicle_name_length]>96&&vehicle_name[vehicle_name_length]<123)
  {
    vehicle_name[vehicle_name_length]=vehicle_name[vehicle_name_length];
  }
}
if(strcmp(vehicle_name,car)==0||strcmp(vehicle_name,truck)==0||strcmp(vehicle_name,bike)==0||strcmp(vehicle_name,bus)==0)
{
  enter_carefully:
    count=0;
printf("enter vehicle_number:");
scanf("\n");
gets(vehicle_number);
int vehicle_number_length=strlen(vehicle_number);
for(vehicle_number_length=0;vehicle_number[vehicle_number_length]!='\0';vehicle_number_length++)
{
if(vehicle_number[vehicle_number_length]>96&&vehicle_number[vehicle_number_length]<123)
{
  vehicle_number[vehicle_number_length]=vehicle_number[vehicle_number_length]-32;
}
else 
{
  vehicle_number[vehicle_number_length]=vehicle_number[vehicle_number_length];
}
}
for(vehicle_number_length=0;vehicle_number[vehicle_number_length]!='\0';vehicle_number_length++)
{
  if((vehicle_number[vehicle_number_length]>-1&&vehicle_number[vehicle_number_length]<48)(vehicle_number[vehicle_number_length]>57&&vehicle_number[vehicle_number_length]<65)(vehicle_number[vehicle_number_length]>90&&vehicle_number[vehicle_number_length]<97)(vehicle_number[vehicle_number_length]>122&&vehicle_number[vehicle_number_length]<128))
{
count++;  
}  
}
if(vehicle_number_length>10||vehicle_number_length<9)
{
  goto enter_carefully;
}
if(vehicle_number_length==9)
{
if((count==0)&&((vehicle_number[2]==48)&&(vehicle_number[3]==48))((vehicle_number[5]==48)&&(vehicle_number[6]==48)&&(vehicle_number[7]==48)&&(vehicle_number[8]==48))((vehicle_number[2]>-1)&&(vehicle_number[2]<48))((vehicle_number[2]>57)&&(vehicle_number[2]<128))((vehicle_number[4]>-1)&&(vehicle_number[4]<65))((vehicle_number[4]>90)&&(vehicle_number[4]<128)))
{
  goto enter_carefully;  
}
}
if(vehicle_number_length==10)
{
if((count==0)&&((vehicle_number[2]==48)&&(vehicle_number[3]==48))((vehicle_number[6]==48)&&(vehicle_number[7]==48)&&(vehicle_number[8]==48)&&(vehicle_number[9]==48))(vehicle_number[2]>-1)&&(vehicle_number[2]<48)(vehicle_number[2]>57)&&(vehicle_number[2]<128)(vehicle_number[4]>-1)&&(vehicle_number[4]<65)(vehicle_number[4]>90)&&(vehicle_number[4]<128)(vehicle_number[5]>-1)&&(vehicle_number[5]<65)(vehicle_number[5]>90)&&(vehicle_number[5]<128)((vehicle_number[2]==48)&&(vehicle_number[3]>64&&vehicle_number[3]<91)))
{
  goto enter_carefully;  
}
}
if(vehicle_number_length==9)
{
  if(((vehicle_number[5]>-1)&&(vehicle_number[5]<48))((vehicle_number[5]>57)&&(vehicle_number[5]<128))((vehicle_number[6]>-1)&&(vehicle_number[6]<48))((vehicle_number[6]>57)&&(vehicle_number[6]<128))((vehicle_number[7]>-1)&&(vehicle_number[7]<48))((vehicle_number[7]>57)&&(vehicle_number[7]<128))((vehicle_number[8]>-1)&&(vehicle_number[8]<48))((vehicle_number[8]>57)&&(vehicle_name[8]<128))((vehicle_number[0]>47)&&(vehicle_number[0]<58))((vehicle_number[1]>47)&&(vehicle_number[1]<58))((vehicle_number[2]==48)&&((vehicle_number[3]>64)&&(vehicle_number[3]<91))))
{
  goto enter_carefully;
}
}
if(vehicle_number_length==10)
{
  if(((vehicle_number[6]>-1)&&(vehicle_number[6]<48))((vehicle_number[6]>57)&&(vehicle_number[6]<128))((vehicle_number[7]>-1)&&(vehicle_number[7]<48))((vehicle_number[7]>57)&&(vehicle_number[7]<128))((vehicle_number[8]>-1)&&(vehicle_number[8]<48))((vehicle_number[8]>57)&&(vehicle_number[8]<128))((vehicle_number[9]>-1)&&(vehicle_number[9]<48))((vehicle_number[9]>57)&&(vehicle_name[9]<128))((vehicle_number[0]>47)&&(vehicle_number[0]<58))((vehicle_number[1]>47)&&(vehicle_number[1]<58))((vehicle_number[2]==48)&&(vehicle_number[3]==48)))
{
  goto enter_carefully;
}
}

if((count==0)&&(vehicle_number_length==9))
  {    
  if(((vehicle_number[0]==65)&&(vehicle_number[1]==80))((vehicle_number[0]==65)&&(vehicle_number[1]==82))((vehicle_number[0]==65)&&(vehicle_number[1]==83))((vehicle_number[0]==66)&&(vehicle_number[1]==82))((vehicle_number[0]==67)&&(vehicle_number[1]==71))((vehicle_number[0]==68)&&(vehicle_number[1]==76))((vehicle_number[0]==71)&&(vehicle_number[1]==65))((vehicle_number[0]==71)&&(vehicle_number[1]==74))((vehicle_number[0]==72)&&(vehicle_number[1]==82))((vehicle_number[0]==72)&&(vehicle_number[1]==80))((vehicle_number[0]==74)&&(vehicle_number[1]==75))((vehicle_number[0]==74)&&(vehicle_number[1]==72))((vehicle_number[0]==75)&&(vehicle_number[1]==65))((vehicle_number[0]==75)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==80))((vehicle_number[0]==77)&&(vehicle_number[1]==72))((vehicle_number[0]==77)&&(vehicle_number[1]==78))((vehicle_number[0]==77)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==90))((vehicle_number[0]==78)&&(vehicle_number[1]==76))((vehicle_number[0]==79)&&(vehicle_number[1]==68))((vehicle_number[0]==79)&&(vehicle_number[1]==82))((vehicle_number[0]==80)&&(vehicle_number[1]==89))((vehicle_number[0]==80)&&(vehicle_number[1]==66))((vehicle_number[0]==82)&&(vehicle_number[1]==74))((vehicle_number[0]==83)&&(vehicle_number[1]==75))((vehicle_number[0]==84)&&(vehicle_number[1]==78))((vehicle_number[0]==84)&&(vehicle_number[1]==83))((vehicle_number[0]==84)&&(vehicle_number[1]==82))((vehicle_number[0]==85)&&(vehicle_number[1]==80))
  ((vehicle_number[0]==85)&&(vehicle_number[1]==75))((vehicle_number[0]==85)&&(vehicle_number[1]==65))((vehicle_number[0]==87)&&(vehicle_number[1]==66))((vehicle_number[0]==65)&&(vehicle_number[1]==78))((vehicle_number[0]==67)&&(vehicle_number[1]==72))((vehicle_number[0]==68)&&(vehicle_number[1]==78))((vehicle_number[0]==68)&&(vehicle_number[1]==68))((vehicle_number[0]==76)&&(vehicle_number[1]==65))((vehicle_number[0]==79)&&(vehicle_number[1]==84))((vehicle_number[4]>64)&&(vehicle_number[4]<91)))
  {
if(((vehicle_number[3]>64)&&(vehicle_number[3]<91)))
      {
      if(((vehicle_number[0]==65)&&(vehicle_number[1]==80))((vehicle_number[0]==65)&&(vehicle_number[1]==82))((vehicle_number[0]==65)&&(vehicle_number[1]==83))((vehicle_number[0]==66)&&(vehicle_number[1]==82))((vehicle_number[0]==67)&&(vehicle_number[1]==71))((vehicle_number[0]==68)&&(vehicle_number[1]==76))((vehicle_number[0]==71)&&(vehicle_number[1]==65))((vehicle_number[0]==71)&&(vehicle_number[1]==74))((vehicle_number[0]==72)&&(vehicle_number[1]==82))((vehicle_number[0]==72)&&(vehicle_number[1]==80))((vehicle_number[0]==74)&&(vehicle_number[1]==75))((vehicle_number[0]==74)&&(vehicle_number[1]==72))((vehicle_number[0]==75)&&(vehicle_number[1]==65))((vehicle_number[0]==75)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==80))((vehicle_number[0]==77)&&(vehicle_number[1]==72))((vehicle_number[0]==77)&&(vehicle_number[1]==78))((vehicle_number[0]==77)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==90))((vehicle_number[0]==78)&&(vehicle_number[1]==76))((vehicle_number[0]==79)&&(vehicle_number[1]==68))((vehicle_number[0]==79)&&(vehicle_number[1]==82))((vehicle_number[0]==80)&&(vehicle_number[1]==89))((vehicle_number[0]==80)&&(vehicle_number[1]==66))((vehicle_number[0]==82)&&(vehicle_number[1]==74))((vehicle_number[0]==83)&&(vehicle_number[1]==75))((vehicle_number[0]==84)&&(vehicle_number[1]==78))((vehicle_number[0]==84)&&(vehicle_number[1]==83))((vehicle_number[0]==84)&&(vehicle_number[1]==82))((vehicle_number[0]==85)&&(vehicle_number[1]==80))((vehicle_number[0]==85)&&(vehicle_number[1]==75))((vehicle_number[0]==85)&&(vehicle_number[1]==65))((vehicle_number[0]==87)&&(vehicle_number[1]==66))((vehicle_number[0]==65)&&(vehicle_number[1]==78))((vehicle_number[0]==67)&&(vehicle_number[1]==72))((vehicle_number[0]==68)&&(vehicle_number[1]==78))((vehicle_number[0]==68)&&(vehicle_number[1]==68))((vehicle_number[0]==76)&&(vehicle_number[1]==65))((vehicle_number[0]==79)&&(vehicle_number[1]==84))((vehicle_number[4]>64)&&(vehicle_number[4]<91)))
  {
     enter_number_carefully_1:
printf("enter vehicle owner mobile number :");
scanf("%lld",&owner_mobile_number);
if((owner_mobile_number<1000000000)(owner_mobile_number>9999999999))
{
  goto enter_number_carefully_1;
}
    }
}
else if((vehicle_number[3]>47)&&(vehicle_number[3]<58))
{if(((vehicle_number[0]==65)&&(vehicle_number[1]==80))((vehicle_number[0]==65)&&(vehicle_number[1]==82))((vehicle_number[0]==65)&&(vehicle_number[1]==83))((vehicle_number[0]==66)&&(vehicle_number[1]==82))((vehicle_number[0]==67)&&(vehicle_number[1]==71))((vehicle_number[0]==68)&&(vehicle_number[1]==76))((vehicle_number[0]==71)&&(vehicle_number[1]==65))((vehicle_number[0]==71)&&(vehicle_number[1]==74))((vehicle_number[0]==72)&&(vehicle_number[1]==82))((vehicle_number[0]==72)&&(vehicle_number[1]==80))((vehicle_number[0]==74)&&(vehicle_number[1]==75))((vehicle_number[0]==74)&&(vehicle_number[1]==72))((vehicle_number[0]==75)&&(vehicle_number[1]==65))((vehicle_number[0]==75)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==80))((vehicle_number[0]==77)&&(vehicle_number[1]==72))((vehicle_number[0]==77)&&(vehicle_number[1]==78))((vehicle_number[0]==77)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==90))((vehicle_number[0]==78)&&(vehicle_number[1]==76))((vehicle_number[0]==79)&&(vehicle_number[1]==68))((vehicle_number[0]==79)&&(vehicle_number[1]==82))((vehicle_number[0]==80)&&(vehicle_number[1]==89))((vehicle_number[0]==80)&&(vehicle_number[1]==66))((vehicle_number[0]==82)&&(vehicle_number[1]==74))((vehicle_number[0]==83)&&(vehicle_number[1]==75))((vehicle_number[0]==84)&&(vehicle_number[1]==78))((vehicle_number[0]==84)&&(vehicle_number[1]==83))((vehicle_number[0]==84)&&(vehicle_number[1]==82))((vehicle_number[0]==85)&&(vehicle_number[1]==80))((vehicle_number[0]==85)&&(vehicle_number[1]==75))((vehicle_number[0]==85)&&(vehicle_number[1]==65))((vehicle_number[0]==87)&&(vehicle_number[1]==66))((vehicle_number[0]==65)&&(vehicle_number[1]==78))((vehicle_number[0]==67)&&(vehicle_number[1]==72))((vehicle_number[0]==68)&&(vehicle_number[1]==78))((vehicle_number[0]==68)&&(vehicle_number[1]==68))((vehicle_number[0]==76)&&(vehicle_number[1]==65))((vehicle_number[0]==79)&&(vehicle_number[1]==84))&&((vehicle_number[4]>64)&&(vehicle_number[4]<91))){
{
  enter_number_carefully_2:
printf("enter vehicle owner mobile number :");
scanf("%d",&owner_mobile_number);
if((owner_mobile_number<1000000000)(owner_mobile_number>9999999999))
{
goto enter_number_carefully_2;
}
}
}
}
else
{
  goto enter_carefully;
}
}
}
else if((count==0)&&(vehicle_number_length==10))
{
if(((vehicle_number[3]>64)&&(vehicle_number[3]<91)))
      {
      if(((vehicle_number[0]==65)&&(vehicle_number[1]==80))((vehicle_number[0]==65)&&(vehicle_number[1]==82))((vehicle_number[0]==65)&&(vehicle_number[1]==83))((vehicle_number[0]==66)&&(vehicle_number[1]==82))((vehicle_number[0]==67)&&(vehicle_number[1]==71))((vehicle_number[0]==68)&&(vehicle_number[1]==76))((vehicle_number[0]==71)&&(vehicle_number[1]==65))((vehicle_number[0]==71)&&(vehicle_number[1]==74))((vehicle_number[0]==72)&&(vehicle_number[1]==82))((vehicle_number[0]==72)&&(vehicle_number[1]==80))((vehicle_number[0]==74)&&(vehicle_number[1]==75))((vehicle_number[0]==74)&&(vehicle_number[1]==72))((vehicle_number[0]==75)&&(vehicle_number[1]==65))((vehicle_number[0]==75)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==80))((vehicle_number[0]==77)&&(vehicle_number[1]==72))((vehicle_number[0]==77)&&(vehicle_number[1]==78))((vehicle_number[0]==77)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==90))((vehicle_number[0]==78)&&(vehicle_number[1]==76))((vehicle_number[0]==79)&&(vehicle_number[1]==68))((vehicle_number[0]==79)&&(vehicle_number[1]==82))((vehicle_number[0]==80)&&(vehicle_number[1]==89))((vehicle_number[0]==80)&&(vehicle_number[1]==66))((vehicle_number[0]==82)&&(vehicle_number[1]==74))((vehicle_number[0]==83)&&(vehicle_number[1]==75))((vehicle_number[0]==84)&&(vehicle_number[1]==78))((vehicle_number[0]==84)&&(vehicle_number[1]==83))((vehicle_number[0]==84)&&(vehicle_number[1]==82))((vehicle_number[0]==85)&&(vehicle_number[1]==80))((vehicle_number[0]==85)&&(vehicle_number[1]==75))((vehicle_number[0]==85)&&(vehicle_number[1]==65))((vehicle_number[0]==87)&&(vehicle_number[1]==66))((vehicle_number[0]==65)&&(vehicle_number[1]==78))((vehicle_number[0]==67)&&(vehicle_number[1]==72))((vehicle_number[0]==68)&&(vehicle_number[1]==78))((vehicle_number[0]==68)&&(vehicle_number[1]==68))((vehicle_number[0]==76)&&(vehicle_number[1]==65))((vehicle_number[0]==79)&&(vehicle_number[1]==84))((vehicle_number[4]>64)&&(vehicle_number[4]<91)))
  {
     enter_number_carefully_3:
printf("enter vehicle owner mobile number :");
scanf("%lld",&owner_mobile_number);
if((owner_mobile_number<1000000000)(owner_mobile_number>9999999999))
{
  goto enter_number_carefully_3;
}
}
}
else if((vehicle_number[3]>47)&&(vehicle_number[3]<58))
{
if(((vehicle_number[0]==65)&&(vehicle_number[1]==80))((vehicle_number[0]==65)&&(vehicle_number[1]==82))((vehicle_number[0]==65)&&(vehicle_number[1]==83))((vehicle_number[0]==66)&&(vehicle_number[1]==82))((vehicle_number[0]==67)&&(vehicle_number[1]==71))((vehicle_number[0]==68)&&(vehicle_number[1]==76))((vehicle_number[0]==71)&&(vehicle_number[1]==65))((vehicle_number[0]==71)&&(vehicle_number[1]==74))((vehicle_number[0]==72)&&(vehicle_number[1]==82))((vehicle_number[0]==72)&&(vehicle_number[1]==80))((vehicle_number[0]==74)&&(vehicle_number[1]==75))((vehicle_number[0]==74)&&(vehicle_number[1]==72))((vehicle_number[0]==75)&&(vehicle_number[1]==65))((vehicle_number[0]==75)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==80))((vehicle_number[0]==77)&&(vehicle_number[1]==72))((vehicle_number[0]==77)&&(vehicle_number[1]==78))((vehicle_number[0]==77)&&(vehicle_number[1]==76))((vehicle_number[0]==77)&&(vehicle_number[1]==90))((vehicle_number[0]==78)&&(vehicle_number[1]==76))((vehicle_number[0]==79)&&(vehicle_number[1]==68))((vehicle_number[0]==79)&&(vehicle_number[1]==82))((vehicle_number[0]==80)&&(vehicle_number[1]==89))((vehicle_number[0]==80)&&(vehicle_number[1]==66))((vehicle_number[0]==82)&&(vehicle_number[1]==74))((vehicle_number[0]==83)&&(vehicle_number[1]==75))((vehicle_number[0]==84)&&(vehicle_number[1]==78))((vehicle_number[0]==84)&&(vehicle_number[1]==83))((vehicle_number[0]==84)&&(vehicle_number[1]==82))((vehicle_number[0]==85)&&(vehicle_number[1]==80))((vehicle_number[0]==85)&&(vehicle_number[1]==75))((vehicle_number[0]==85)&&(vehicle_number[1]==65))((vehicle_number[0]==87)&&(vehicle_number[1]==66))((vehicle_number[0]==65)&&(vehicle_number[1]==78))((vehicle_number[0]==67)&&(vehicle_number[1]==72))((vehicle_number[0]==68)&&(vehicle_number[1]==78))((vehicle_number[0]==68)&&(vehicle_number[1]==68))((vehicle_number[0]==76)&&(vehicle_number[1]==65))((vehicle_number[0]==79)&&(vehicle_number[1]==84))&&((vehicle_number[4]>64)&&(vehicle_number[4]<91))){
{
  enter_number_carefully_4:
printf("enter vehicle owner mobile number :");
scanf("%d",&owner_mobile_number);
if((owner_mobile_number<1000000000)(owner_mobile_number>9999999999))
{
goto enter_number_carefully_4;
}
}
}
}
}
}
else
{
  printf("we do not park this vehicle\n");
  time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
}
if(strcmp(vehicle_name,car)==0)
{
car_information=fopen("car_park_details","r");
fread(CAR,sizeof(struct car_vehicle),information_of_space_cost[1],car_information);
fclose(car_information);
for(car_space=0;car_space<information_of_space_cost[1];car_space++)
{
  if(CAR[car_space].car_owner_mobile_number==owner_mobile_number)
  {
    break;
  }
}
if(CAR[car_space].car_owner_mobile_number==owner_mobile_number)
{
printf("your car was parked in car_%d\n",car_space+1);
time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
CAR[car_space].car_owner_mobile_number=0;
for(g=0;g<12;g++)
{
CAR[car_space].car_number[g]=vehicle_no[g];  
}
for(h=0;h<30;h++)
{
CAR[car_space].car_owner_name[h]=name[h];  
}
 days=(s-CAR[car_space].car_seconds)/(24*3600);
 if(days==0)
 {
 printf("bill for 1 days parking is %d Rs.",information_of_space_cost[2]);  
 }
 else
 {
 printf("bill for %d days parking is %ld Rs.",days,days*information_of_space_cost[2]);
}
}
else
{
  for(car_space=0;car_space<information_of_space_cost[1];car_space++)
  {
    if(CAR[car_space].car_owner_mobile_number==0)
    {
      break;
    }
  }
  CAR[car_space].car_owner_mobile_number=owner_mobile_number;
  for(g=0;g<12;g++)
  {
    CAR[car_space].car_number[g]=vehicle_number[g];
  }
  for(h=0;h<30;h++)
  {
    CAR[car_space].car_owner_name[h]=owner_name[h];
  }
  printf("park your car in car_%d\n",car_space+1);
  time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
        CAR[car_space].car_seconds=s;
}
car_information=fopen("car_park_details","wb");
fwrite(CAR,sizeof(struct car_vehicle),information_of_space_cost[1],car_information);
fclose(car_information);  
}
if(strcmp(vehicle_name,truck)==0)
{
truck_information=fopen("truck_park_details","r");
fread(TRUCK,sizeof(struct truck_vehicle),information_of_space_cost[3],truck_information);
fclose(truck_information);
for(truck_space=0;truck_space<information_of_space_cost[3];truck_space++)
{
  if(TRUCK[truck_space].truck_owner_mobile_number==owner_mobile_number)
  {
    break;
  }
}
if(TRUCK[truck_space].truck_owner_mobile_number==owner_mobile_number)
{
printf("your truck was parked in truck_%d\n",truck_space+1);
time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
TRUCK[truck_space].truck_owner_mobile_number=0;
for(g=0;g<12;g++)
{
TRUCK[truck_space].truck_number[g]=vehicle_no[g];  
}
for(h=0;h<30;h++)
{
TRUCK[truck_space].truck_owner_name[h]=name[h];  
}
days=(s-TRUCK[truck_space].truck_seconds)/(24*3600);
 if(days==0)
 {
 printf("bill for 1 days parking is %d Rs.",information_of_space_cost[4]);  
 }
 else
 {
 printf("bill for %d days parking is %ld Rs.",days,days*information_of_space_cost[4]);
}  
}
else
{
  for(truck_space=0;truck_space<information_of_space_cost[3];truck_space++)
  {
    if(TRUCK[truck_space].truck_owner_mobile_number==0)
    {
      break;
    }
  }
  TRUCK[truck_space].truck_owner_mobile_number=owner_mobile_number;
  for(g=0;g<12;g++)
  {
    TRUCK[truck_space].truck_number[g]=vehicle_number[g];
  }
  for(h=0;h<30;h++)
  {
    TRUCK[truck_space].truck_owner_name[h]=owner_name[h];
  }
  printf("park your truck in truck_%d\n",truck_space+1);
  time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
        TRUCK[truck_space].truck_seconds=s;
}
truck_information=fopen("truck_park_details","wb");
fwrite(TRUCK,sizeof(struct truck_vehicle),information_of_space_cost[3],truck_information);
fclose(truck_information);  
}
if(strcmp(vehicle_name,bike)==0)
{
bike_information=fopen("bike_park_details","r");
fread(BIKE,sizeof(struct bike_vehicle),information_of_space_cost[5],bike_information);
fclose(bike_information);
for(bike_space=0;bike_space<information_of_space_cost[5];bike_space++)
{
  if(BIKE[bike_space].bike_owner_mobile_number==owner_mobile_number)
  {
    break;
  }
}
if(BIKE[bike_space].bike_owner_mobile_number==owner_mobile_number)
{
printf("your bike was parked in bike_%d\n",bike_space+1);
time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
BIKE[bike_space].bike_owner_mobile_number=0;
for(g=0;g<12;g++)
{
BIKE[bike_space].bike_number[g]=vehicle_no[g];  
}
for(h=0;h<30;h++)
{
BIKE[bike_space].bike_owner_name[h]=name[h];  
}
days=(s-BIKE[bike_space].bike_seconds)/(24*3600);
 if(days==0)
 {
 printf("bill for 1 days parking is %d Rs.",information_of_space_cost[6]);  
 }
 else
 {printf("bill for %d days parking is %ld Rs.",days,days*information_of_space_cost[6]);
}  
}
else
{
  for(bike_space=0;bike_space<information_of_space_cost[5];bike_space++)
  {
    if(BIKE[bike_space].bike_owner_mobile_number==0)
    {
      break;
    }
  }
  BIKE[bike_space].bike_owner_mobile_number=owner_mobile_number;
  for(g=0;g<12;g++)
  {
    BIKE[bike_space].bike_number[g]=vehicle_number[g];
  }
  for(h=0;h<30;h++)
  {
    BIKE[bike_space].bike_owner_name[h]=owner_name[h];
  }
  printf("park your bike in bike_%d\n",bike_space+1);
  time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
        BIKE[bike_space].bike_seconds=s;
}
bike_information=fopen("bike_park_details","wb");
fwrite(BIKE,sizeof(struct bike_vehicle),information_of_space_cost[5],bike_information);
fclose(bike_information);  
}
if(strcmp(vehicle_name,bus)==0)
{
bus_information=fopen("bus_park_details","r");
fread(BUS,sizeof(struct bus_vehicle),information_of_space_cost[7],bus_information);
fclose(bus_information);
for(bus_space=0;bus_space<information_of_space_cost[7];bus_space++)
{
  if(BUS[bus_space].bus_owner_mobile_number==owner_mobile_number)
  {
    break;
  }
}
if(BUS[bus_space].bus_owner_mobile_number==owner_mobile_number)
{
printf("your bus was parked in bus_%d\n",bus_space+1);
time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
BUS[bus_space].bus_owner_mobile_number=0;
for(g=0;g<12;g++)
{
BUS[bus_space].bus_number[g]=vehicle_no[g];  
}
for(h=0;h<30;h++)
{
BUS[bus_space].bus_owner_name[h]=name[h];  
}
days=(s-CAR[car_space].car_seconds)/(24*3600);
 if(days==0)
 {
 printf("bill for 1 days parking is %d Rs.",information_of_space_cost[8]);  
 }
 else
 {
 printf("bill for %d days parking is %ld Rs.",days,days*information_of_space_cost[8]);
}  
}
else
{
  for(bus_space=0;bus_space<information_of_space_cost[7];bus_space++)
  {
    if(BUS[bus_space].bus_owner_mobile_number==0)
    {
      break;
    }
  }
  BUS[bus_space].bus_owner_mobile_number=owner_mobile_number;
  for(g=0;g<12;g++)
  {
    BUS[bus_space].bus_number[g]=vehicle_number[g];
  }
  for(h=0;h<30;h++)
  {
    BUS[bus_space].bus_owner_name[h]=owner_name[h];
  }
  printf("park your bus in bus_%d\n",bus_space+1);
  time_t s;
        struct tm* curr_time;
        s=time(NULL);
        curr_time = localtime(&s);
        printf("%02d:%02d:%02d\t\t",curr_time->tm_hour,curr_time->tm_min,curr_time->tm_sec);
        strftime(date_string,20,"%d-%m-%y",curr_time);
        printf("%s\n",date_string);
        BUS[bus_space].bus_seconds=s;
}
bus_information=fopen("bus_park_details","wb");
fwrite(BUS,sizeof(struct bus_vehicle),information_of_space_cost[7],bus_information);
fclose(bus_information);  
}
}
return 0;
}
