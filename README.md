# provider {
  region = "ap_south_1"
}

resource "aws_instance" "my-terraform" {
  ami           = " ami-02b8269d5e85954ef "
  instance_type = "var.ami"
  vpc_security_group_ids = ["aws_security_group.aws_sg.id "]
  region = "ap-south-1"
  

  tags = {
    env = "dev"
  }

}

  resource "security_group" "aws_sg"{ 
    name = "sg-name"
    description = " allow http inbound and all outbiund traffic "
    vpc_id = "vpc-0423b95e2e5453a5c"


    ingress {
      from port = 80
      to_port = 80
      protocol = "tcp"
      cidr_blocks = ["0.0.0.0/0"]
    }


    egress {
      from_port = 0
      to_port = 0 
      protocol = " -1"
    }
  
  }

  


