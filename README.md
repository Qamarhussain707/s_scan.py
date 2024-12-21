# s_scan.py
import socket

def scan_ports(target_ip, start_port, end_port):
    print(f"Scanning {target_ip} from port {start_port} to {end_port}...")

    # Loop through each port in the specified range
    for port in range(start_port, end_port + 1):
        sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        sock.settimeout(1)  # 1-second timeout for each connection attempt

        # Attempt to connect to the target IP and port
        result = sock.connect_ex((target_ip, port))

        if result == 0:
            print(f"Port {port} is open")
        else:
            print(f"Port {port} is closed")
        
        sock.close()

def main():
    target_ip = input("Enter the IP address to scan: ")
    start_port = int(input("Enter the starting port: "))
    end_port = int(input("Enter the ending port: "))
    
    # Start the scan
    scan_ports(target_ip, start_port, end_port)

if _name_ == "_main_":
    main()
