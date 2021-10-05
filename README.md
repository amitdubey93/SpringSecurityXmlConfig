# Setup Database.

I'm using Mysql.
Database name: simplehr

```
-- Create table
create table USERS
(
  USERNAME VARCHAR(36) not null,
  PASSWORD VARCHAR(36) not null,
  ENABLED  smallint not null
) ;

alter table USERS
  add constraint USER_PK primary key (USERNAME);

---------------------

-- Create table
create table USER_ROLES
(
  ROLE_ID   VARCHAR(50) not null,
  USERNAME  VARCHAR(36) not null,
  USER_ROLE VARCHAR(30) not null
) ;
 
alter table USER_ROLES
  add constraint USER_ROLE_PK primary key (ROLE_ID);

alter table USER_ROLES
  add constraint USER_ROLE_UK unique (USERNAME, USER_ROLE);
 
-------------------------------
 
insert into users (USERNAME, PASSWORD, ENABLED)
values ('dbuser1', '12345', 1);

insert into users (USERNAME, PASSWORD, ENABLED)
values ('dbadmin1', '12345', 1);  


insert into User_Roles (ROLE_ID, USERNAME, USER_ROLE)
values ('1', 'dbuser1', 'USER');

insert into User_Roles (ROLE_ID, USERNAME, USER_ROLE)
values ('2', 'dbadmin1', 'ADMIN');

insert into User_Roles (ROLE_ID, USERNAME, USER_ROLE)
values ('3', 'dbadmin1', 'USER');

```