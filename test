SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0;
SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0;
SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='TRADITIONAL,ALLOW_INVALID_DATES';

-- -----------------------------------------------------
-- Schema mydb
-- -----------------------------------------------------
-- -----------------------------------------------------
-- Schema hospitaldb
-- -----------------------------------------------------

-- -----------------------------------------------------
-- Schema hospitaldb
-- -----------------------------------------------------
CREATE SCHEMA IF NOT EXISTS `hospitaldb` DEFAULT CHARACTER SET utf8 ;
USE `hospitaldb` ;

-- -----------------------------------------------------
-- Table `hospitaldb`.`department`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`department` (
  `dept_id` INT(11) NOT NULL AUTO_INCREMENT,
  `dept_name` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`dept_id`),
  UNIQUE INDEX `dept_id_UNIQUE` (`dept_id` ASC))
ENGINE = InnoDB
AUTO_INCREMENT = 19
DEFAULT CHARACTER SET = utf8;


-- -----------------------------------------------------
-- Table `hospitaldb`.`diagnosis`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`diagnosis` (
  `dgns_id` INT(11) NOT NULL AUTO_INCREMENT,
  `dgns_name` VARCHAR(45) NOT NULL,
  `dept_id` INT(11) NOT NULL,
  PRIMARY KEY (`dgns_id`),
  UNIQUE INDEX `dgns_id_UNIQUE` (`dgns_id` ASC),
  INDEX `fk_diagnosis_department` (`dept_id` ASC),
  CONSTRAINT `fk_diagnosis_department`
    FOREIGN KEY (`dept_id`)
    REFERENCES `hospitaldb`.`department` (`dept_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB
AUTO_INCREMENT = 21
DEFAULT CHARACTER SET = utf8;


-- -----------------------------------------------------
-- Table `hospitaldb`.`doctor`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`doctor` (
  `doc_id` INT(11) NOT NULL AUTO_INCREMENT,
  `doc_fullname` VARCHAR(45) NOT NULL,
  `doc_dob` DATE NOT NULL,
  `doc_gender` CHAR(1) NOT NULL,
  `dept_id` INT(11) NOT NULL,
  PRIMARY KEY (`doc_id`),
  UNIQUE INDEX `doc_id_UNIQUE` (`doc_id` ASC),
  INDEX `fk_doctor_dept` (`dept_id` ASC),
  CONSTRAINT `fk_doctor_dept`
    FOREIGN KEY (`dept_id`)
    REFERENCES `hospitaldb`.`department` (`dept_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB
AUTO_INCREMENT = 101
DEFAULT CHARACTER SET = utf8;


-- -----------------------------------------------------
-- Table `hospitaldb`.`patient`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`patient` (
  `pat_id` INT(11) NOT NULL AUTO_INCREMENT,
  `pat_fullname` VARCHAR(45) NOT NULL,
  `pat_dob` DATE NOT NULL,
  `pat_gender` CHAR(1) NOT NULL,
  `pat_email` VARCHAR(45) NOT NULL,
  `pat_address` VARCHAR(255) NOT NULL,
  PRIMARY KEY (`pat_id`),
  UNIQUE INDEX `idpatient_UNIQUE` (`pat_id` ASC))
ENGINE = InnoDB
AUTO_INCREMENT = 101
DEFAULT CHARACTER SET = utf8;


-- -----------------------------------------------------
-- Table `hospitaldb`.`treatment`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`treatment` (
  `tret_id` INT(11) NOT NULL AUTO_INCREMENT,
  `tret_name` VARCHAR(45) NOT NULL,
  PRIMARY KEY (`tret_id`))
ENGINE = InnoDB
AUTO_INCREMENT = 10
DEFAULT CHARACTER SET = utf8;


-- -----------------------------------------------------
-- Table `hospitaldb`.`diagnosis-treatment`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`diagnosis-treatment` (
  `dgns_tret_id` INT(11) NOT NULL AUTO_INCREMENT,
  `dgns_id` INT(11) NOT NULL,
  `pat_id` INT(11) NOT NULL,
  `tret_id` INT(11) NOT NULL,
  `doc_id` INT(11) NOT NULL,
  `diagtret_date` DATE NOT NULL,
  PRIMARY KEY (`dgns_tret_id`),
  UNIQUE INDEX `dgns_tret_id_UNIQUE` (`dgns_tret_id` ASC),
  INDEX `fk_diagtret_patient` (`pat_id` ASC),
  INDEX `fk_diagtret_doctor` (`doc_id` ASC),
  INDEX `fk_diagtret_treatment` (`tret_id` ASC),
  INDEX `fk_diagtret_diagnosis` (`dgns_id` ASC),
  CONSTRAINT `fk_diagtret_diagnosis`
    FOREIGN KEY (`dgns_id`)
    REFERENCES `hospitaldb`.`diagnosis` (`dgns_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_diagtret_doctor`
    FOREIGN KEY (`doc_id`)
    REFERENCES `hospitaldb`.`doctor` (`doc_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_diagtret_patient`
    FOREIGN KEY (`pat_id`)
    REFERENCES `hospitaldb`.`patient` (`pat_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION,
  CONSTRAINT `fk_diagtret_treatment`
    FOREIGN KEY (`tret_id`)
    REFERENCES `hospitaldb`.`treatment` (`tret_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB
AUTO_INCREMENT = 21
DEFAULT CHARACTER SET = utf8;


-- -----------------------------------------------------
-- Table `hospitaldb`.`nurse`
-- -----------------------------------------------------
CREATE TABLE IF NOT EXISTS `hospitaldb`.`nurse` (
  `nrs_id` INT(11) NOT NULL AUTO_INCREMENT,
  `nrs_fullname` VARCHAR(45) NOT NULL,
  `nrs_dob` DATE NOT NULL,
  `nrs_gender` CHAR(1) NOT NULL,
  `doc_id` INT(11) NOT NULL,
  PRIMARY KEY (`nrs_id`),
  UNIQUE INDEX `idnurse_UNIQUE` (`nrs_id` ASC),
  INDEX `fk_nurse_doctor` (`doc_id` ASC),
  CONSTRAINT `fk_nurse_doctor`
    FOREIGN KEY (`doc_id`)
    REFERENCES `hospitaldb`.`doctor` (`doc_id`)
    ON DELETE NO ACTION
    ON UPDATE NO ACTION)
ENGINE = InnoDB
AUTO_INCREMENT = 101
DEFAULT CHARACTER SET = utf8;


SET SQL_MODE=@OLD_SQL_MODE;
SET FOREIGN_KEY_CHECKS=@OLD_FOREIGN_KEY_CHECKS;
SET UNIQUE_CHECKS=@OLD_UNIQUE_CHECKS;
