The hardware can be broken down by stage.

![[Pasted image 20231127171230.png| 600]]

# Stage Partitions

Barriers are special registers that hold values between stages.

![[Pasted image 20231127171331.png]]

# Forwarding

Forwarding requires another control unit.

![[Pasted image 20231127171413.png]]

For ALU to ALU forwarding, the value from the ALU is piped back around to the mux preceding the ALU. The Forwarding unit then selects this value.

For MEM to ALU forwarding, the value from the ALU is piped back around to the mux preceding the ALU. The Forwarding unit then selects this value.

# Controls

![[Pasted image 20231127171923.png | 700]]

The controls have to be saved between stages and are used in the appropriate stage. 
