drop function if exists ShowUserWrongId;
drop procedure if exists ShowUserById;

DELIMITER $$

create function ShowUserWrongId() returns varchar(30) deterministic
	begin
		return "Error - wrong user id";
	end $$

create procedure ShowUserById(userId bigint)
	begin
		if userId > 0 then
			SELECT * FROM kodilla_course.users where ID = userId;
		else
			select ShowUserWrongId() as message;
		end if;
	end $$
    
DELIMITER ;

call ShowUserById(0);
