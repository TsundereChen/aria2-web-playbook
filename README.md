# aria2-web-playbook

This is an Ansible Playbook to help you create your own aria2 download site

## Usage
* You should run this playbook on `Ubuntu`
* Need to enable `universe` repo in `apt` first
* Copy `inventory.sample` to `inventory`, then modify content according to the file
* `ansible-playbook -i inventory aria2-web-playbook.yaml`
* It's recommended to run this playbook using `root`, or using normal user with passwordless `sudo` permission

## Notes
* The download site will be at `https://<DOMAIN>`, and you can download your file at `https://<DOMAIN>/downloads`
* In order to enhance security, it's recommended that after you run this playbook, you manually add http-auth

## Add http-auth
* Install `apache2-utils`
* Run `htpasswd -c /etc/nginx/.htpasswd <USERNAME>` to create new user, and remember to set file's permission properly
* Add these lines into `/jsonrpc` and `/downloads` block, this will prevent others from reading your tasks
  ```
  auth_basic "Not avaliable";
  auth_basic_user_file /etc/nginx/.htpasswd
  ```

