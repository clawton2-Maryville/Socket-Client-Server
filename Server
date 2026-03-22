import socket
import threading

HOST = "0.0.0.0"
PORT = 9500

def handle_client(conn, addr):
    print(f"Connected by {addr}")
    data = conn.recv(1024).decode().strip()

    if data == "Hello":
        response = "Hi"
    else:
        response = "Goodbye"

    conn.sendall(response.encode())
    conn.close()
    print(f"Connection closed {addr}")

def start_server():
    with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
        s.bind((HOST, PORT))
        s.listen()

        print("Server listening on port 9500...")

        while True:
            conn, addr = s.accept()
            thread = threading.Thread(target=handle_client, args=(conn, addr))
            thread.start()

if __name__ == "__main__":
    start_server()
