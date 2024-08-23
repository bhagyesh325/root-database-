create database tours;
<br>
use tours;
<br>
create table website (
website_id VARCHAR(20) primary key,
name VARCHAR(20),
section VARCHAR(20),
links VARCHAR(20),
Agency_logo BLOB
);
<br>
create table users (
User_id VARCHAR(20) primary key,
Admin_id VARCHAR(20),
Role VARCHAR(20),
Profile_photo BLOB,
Name VARCHAR(50),
Age INT,
Gender CHAR(10),
Mob_no VARCHAR(10),
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME
);
<br>
create table tourists (
Tourist_id VARCHAR(50) primary key,
Nationality VARCHAR(20),
Preferences VARCHAR(20),
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Tourist_id) references users(User_id)
);
<br>
create table tourist_guide (
Tourist_id VARCHAR(50) primary key,
Preference VARCHAR(20),
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Tourist_id) references tourists(Tourist_id)
);
<br>
create table locations (
Location_id VARCHAR(50) primary key,
Place_name VARCHAR(50),
Visit_date DATETIME,
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Location_id) references tourists(Tourist_id)
);
<br>
create table agencies (
Agency_id VARCHAR(50) primary key,
Name VARCHAR(50),
Mobile_No VARCHAR(15),
Email_Address VARCHAR(20),
Address VARCHAR(150),
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME
);
<br>
create table Accomodations (
Accomodation_id VARCHAR(50) primary key,
Accomodation_details VARCHAR(50),
Name VARCHAR(20),
Price DECIMAL(10,0),
Accomodation_Images BLOB,
Rating DECIMAL(10,0),
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Accomodation_id) references agencies(Agency_id)
);
<br>
create table Accomodation_types (
Accomodation_Type_id VARCHAR(50) primary key,
Hotel_info VARCHAR(50),
Hotel_images BLOB,
GuestHouses_info VARCHAR(50),
GuestHouses_images BLOB,
Hostels_info VARCHAR(50),
Hostels_images BLOB,
Camping_info VARCHAR(50),
Camping_images BLOB,
Lodges_info VARCHAR(50),
Lodges_images BLOB,
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Accomodation_Type_id) references Accomodations(Accomodation_id)
);
<br>
create table reviews (
Comment VARCHAR(200),
Review_date DATETIME,
Rating DECIMAL(10,0),
Review_id VARCHAR(50) primary key,
images BLOB,
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Review_id) references agencies(Agency_id),
foreign key (Review_id) references users(User_id)
);
<br>
create table tours (
Tour_id VARCHAR(50) primary key,
Name VARCHAR(50),
Iteneraries text,
Need_to_Know text,
Tour_details text,
Tour_Information text,
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Tour_id) references agencies(Agency_id),
foreign key (Tour_id) references users(User_id)
);
<br>
create table policy_terms (
Policy_terms_id VARCHAR(50) primary key,
Policy_term_details text,
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Policy_terms_id) references tours(Tour_id)
);
<br>
create table bookings (
Booking_id VARCHAR(50) primary key,
Status VARCHAR(20),
Booking_date DATETIME,
created_by VARCHAR(50),
created_on DATETIME,
Update_on VARCHAR(50),
Updated_by DATETIME,
Deleted_on VARCHAR(50),
Deleted_by DATETIME,
foreign key (Booking_id) references tours(Tour_id),
foreign key (Booking_id) references Accomodations(Accomodation_id)
);# root-database-
