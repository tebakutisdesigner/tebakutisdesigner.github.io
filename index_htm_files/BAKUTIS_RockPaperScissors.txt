--=======================================
-- function:  SeedRandom
-- author:    Eric Bakutis
-- created:   July 17, 2007
-- returns:   n/a
-- descript:  This function will seed the random number generator by grabbing
--            the current value from the computer's time
--=======================================
function SeedRandom()
    --grab the time from the OS and take the Day, Month, Year, Hour, Minute,
    --Second and build them into a number e.g. 7122007104535
    math.randomseed(os.time())

    --start a loop that will run the random function 3 times to 'prime' it
    for i = 1,3 do
        --pick a number between 1 and 10 based on our random seed, priming
        math.random(1,10)
    end
end


--=======================================
-- function:  RockPaperScissors
-- author:    Eric Bakutis
-- created:   June 19, 2008
-- returns:   n/a
-- descript:  Gets a sign from the player, then plays Rock-Paper-Scissors
--=======================================
function RockPaperScissors(UserMove)

    --hold the player's choice
    local UserMove

	--define a local variable to hold the winner and loser
	--use 0 for tie, 1 for player win, 2 for computer win
	local iGameWinner
	
	--define a local variable to hold the computer's sign
	local sComputerSign
	
	--get a random number from 1 to 3 to determine computer sign thrown
	local ComputerMove = math.random(1,3)
	
	--get a sign for the player
    input = io.input(io.stdin)

    local line
    print("Please enter rock, paper, or scissors and press enter:")
    --this loop waits until it encounters a 4 character then breaks out of the repeat loop
    --repeat
        --input:seek("set")
        UserMove = input:read()
        --if string.len(line) > 4 then
            --break  --this break out of the loop
        --end
    --until endOfTime

    print("You entered the following sign: " .. UserMove)
    input:close()

	--set the computer's thrown sign based on the random number
	if (ComputerMove <= 1) then
		ComputerSign = "rock"

		--now that we know the computer's sign, compare the winner or loser
		--in the same function for efficiency
		if (UserMove == "rock") then
			--rock and rock tie
			print(UserMove .. " ties " .. ComputerSign)
			print("It's a tie!")
			iGameWinner = 0
		end

		if (UserMove == "paper") then
			--paper beats rock, player wins
			print(UserMove .. " covers " .. ComputerSign)
			print("User wins!")
			iGameWinner = 1
		end

		if (UserMove == "scissors") then
			--scissors beats rock tie
			print(ComputerSign .. " beats " .. UserMove)
			print("Computer wins!")
			iGameWinner = 2
		end

	end

	if (ComputerMove > 1 and ComputerMove <= 2) then
		ComputerSign = "paper"

		--now that we know the computer's sign, compare the winner or loser
		--in the same function for efficiency
		if (UserMove == "paper") then
			--paper and paper tie
			print(UserMove .. " ties " .. ComputerSign)
			print("It's a tie!")
			iGameWinner = 0
		end

		if (UserMove == "scissors") then
			--scissors beats paper, player wins
			print(UserMove .. " beats " .. ComputerSign)
			print("User wins!")
			iGameWinner = 1
		end

		if (UserMove == "rock") then
			--paper covers rock
			print(ComputerSign .. " covers " .. UserMove)
			print("Computer wins!")
			iGameWinner = 2
		end			

	end
		
	if (ComputerMove > 2 and ComputerMove <= 3) then
		ComputerSing = "scissors"
		
		--now that we know the computer's sign, compare the winner or loser
		--in the same function for efficiency
		if (UserMove == "scissors") then
			--scissors and scissors tie
			print(UserMove .. " ties " .. ComputerSign)
			print("It's a tie!")
			iGameWinner = 0
		end

		if (UserMove == "rock") then
			--rock beats scissors, player wins
			print(UserMove .. " beats " .. ComputerSign)
			print("User wins!")
			iGameWinner = 1
		end

		if (UserMove == "paper") then
			--scissors cut paper
			print(ComputerSign .. " beats " .. UserMove)
			print("Computer wins!")
			iGameWinner = 2
		end

	end

	print("Game completed")
	print("GameWinner value was " .. iGameWinner)

end