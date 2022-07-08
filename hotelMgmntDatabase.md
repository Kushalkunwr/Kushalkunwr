-- MariaDB dump 10.19  Distrib 10.4.18-MariaDB, for Win64 (AMD64)
--
-- Host: localhost    Database: The_Light_Hotel
-- ------------------------------------------------------
-- Server version	10.4.18-MariaDB

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
/*!40101 SET NAMES utf8mb4 */;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `booking_details`
--

DROP TABLE IF EXISTS `booking_details`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `booking_details` (
  `Booking_id` int(11) NOT NULL AUTO_INCREMENT,
  `Customer_id` int(11) DEFAULT NULL,
  `Check_in_date` date NOT NULL,
  `Check_out_date` date NOT NULL,
  PRIMARY KEY (`Booking_id`),
  KEY `Customer_id` (`Customer_id`),
  CONSTRAINT `booking_details_ibfk_1` FOREIGN KEY (`Customer_id`) REFERENCES `customers` (`Customer_id`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `booking_details`
--

LOCK TABLES `booking_details` WRITE;
/*!40000 ALTER TABLE `booking_details` DISABLE KEYS */;
INSERT INTO `booking_details` VALUES (1,1,'2020-12-01','2020-12-15'),(2,2,'2020-12-05','2020-12-10'),(3,3,'2020-12-13','2020-12-20'),(4,4,'2020-12-18','2020-12-20'),(5,5,'2020-12-20','2020-12-25'),(6,6,'2020-12-30','2021-01-01'),(7,7,'2020-01-01','2021-01-03');
/*!40000 ALTER TABLE `booking_details` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `customers`
--

DROP TABLE IF EXISTS `customers`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `customers` (
  `Customer_id` int(11) NOT NULL AUTO_INCREMENT,
  `Name` varchar(100) DEFAULT NULL,
  `Phone_no` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`Customer_id`)
) ENGINE=InnoDB AUTO_INCREMENT=8 DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `customers`
--

LOCK TABLES `customers` WRITE;
/*!40000 ALTER TABLE `customers` DISABLE KEYS */;
INSERT INTO `customers` VALUES (1,'Edward','2147483647'),(2,'Beerus','2147483647'),(3,'Evana','2147483647'),(4,'Eren','2147483647'),(5,'Kirito','1593698521'),(6,'Gray','2147483647'),(7,'Erza','2147483647');
/*!40000 ALTER TABLE `customers` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `employees`
--

DROP TABLE IF EXISTS `employees`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `employees` (
  `Employee_id` int(11) NOT NULL AUTO_INCREMENT,
  `Name` varchar(20) NOT NULL,
  `Designation` varchar(20) DEFAULT 'Unspecified',
  `Address` varchar(20) DEFAULT NULL,
  `Phone_no` varchar(20) DEFAULT NULL,
  PRIMARY KEY (`Employee_id`)
) ENGINE=InnoDB AUTO_INCREMENT=21 DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `employees`
--

LOCK TABLES `employees` WRITE;
/*!40000 ALTER TABLE `employees` DISABLE KEYS */;
INSERT INTO `employees` VALUES (1,'Kakashi','Manager','Khokana','1326548795'),(2,'Hinata','Manager','Hiledol','2147483647'),(3,'Hinata','Manager','Hiledol','2147483647'),(4,'Sasuke','Manager','Bhainsepati','2147483647'),(5,'Krillin','Bellboy','Basantapur','2147483647'),(6,'Obito','Bellboy','Chovar','2147483647'),(7,'Rin','Room service staff','Chovar','2147483647'),(8,'Rin','Room service staff','Old Baneshwor','2147483647'),(9,'Asuna','Room service staff','New Baneshwor','2147483647'),(10,'Grey','Unspecified','Gongabu','2147483647');
/*!40000 ALTER TABLE `employees` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `rooms`
--

DROP TABLE IF EXISTS `rooms`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `rooms` (
  `Room_ID` int(11) NOT NULL AUTO_INCREMENT,
  `Room_no` int(11) DEFAULT NULL,
  `Room_type` varchar(10) NOT NULL,
  `Booking_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`Room_ID`),
  UNIQUE KEY `Room_no` (`Room_no`),
  KEY `Booking_id` (`Booking_id`),
  CONSTRAINT `rooms_ibfk_1` FOREIGN KEY (`Booking_id`) REFERENCES `booking_details` (`Booking_id`)
) ENGINE=InnoDB AUTO_INCREMENT=13 DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `rooms`
--

LOCK TABLES `rooms` WRITE;
/*!40000 ALTER TABLE `rooms` DISABLE KEYS */;
INSERT INTO `rooms` VALUES (1,1001,'Non-AC',4),(2,1002,'AC',2),(3,1003,'Non-AC',1),(4,1004,'AC',1),(5,2001,'Non-AC',3),(6,2002,'AC',5),(7,2003,'Non-AC',6),(8,2004,'AC',6),(9,3001,'Non-AC',7),(10,3002,'AC',7),(11,3003,'Non-AC',7),(12,3004,'AC',5);
/*!40000 ALTER TABLE `rooms` ENABLE KEYS */;
UNLOCK TABLES;

--
-- Table structure for table `services`
--

DROP TABLE IF EXISTS `services`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
/*!40101 SET character_set_client = utf8 */;
CREATE TABLE `services` (
  `Service_id` int(11) NOT NULL AUTO_INCREMENT,
  `Room_id` int(11) DEFAULT NULL,
  `Employee_id` int(11) DEFAULT NULL,
  PRIMARY KEY (`Service_id`),
  KEY `Room_id` (`Room_id`),
  KEY `Employee_id` (`Employee_id`),
  CONSTRAINT `services_ibfk_1` FOREIGN KEY (`Room_id`) REFERENCES `rooms` (`Room_ID`),
  CONSTRAINT `services_ibfk_2` FOREIGN KEY (`Employee_id`) REFERENCES `employees` (`Employee_id`)
) ENGINE=InnoDB AUTO_INCREMENT=37 DEFAULT CHARSET=utf8mb4;
/*!40101 SET character_set_client = @saved_cs_client */;

--
-- Dumping data for table `services`
--

LOCK TABLES `services` WRITE;
/*!40000 ALTER TABLE `services` DISABLE KEYS */;
INSERT INTO `services` VALUES (1,1,1),(2,2,1),(3,3,1),(4,4,1),(5,5,2),(6,6,2),(7,7,2),(8,8,2),(9,9,3),(10,10,3),(11,11,3),(12,12,3),(13,1,4),(14,2,4),(15,3,4),(16,4,4),(17,5,5),(18,6,5),(19,7,5),(20,8,5),(21,9,6),(22,10,6),(23,11,6),(24,12,6),(25,1,7),(26,2,7),(27,3,7),(28,4,7),(29,5,8),(30,6,8),(31,7,8),(32,8,8),(33,9,9),(34,10,9),(35,11,9),(36,12,9);
/*!40000 ALTER TABLE `services` ENABLE KEYS */;
UNLOCK TABLES;
/*!40103 SET TIME_ZONE=@OLD_TIME_ZONE */;

/*!40101 SET SQL_MODE=@OLD_SQL_MODE */;
/*!40014 SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS */;
/*!40014 SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS */;
/*!40101 SET CHARACTER_SET_CLIENT=@OLD_CHARACTER_SET_CLIENT */;
/*!40101 SET CHARACTER_SET_RESULTS=@OLD_CHARACTER_SET_RESULTS */;
/*!40101 SET COLLATION_CONNECTION=@OLD_COLLATION_CONNECTION */;
/*!40111 SET SQL_NOTES=@OLD_SQL_NOTES */;

-- Dump completed on 2021-04-28 23:13:20
