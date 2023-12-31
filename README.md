
# Dedecms-v5.7.109-RCE

Since CVE-2022-43192 is not fully fixed, Dedecms still has a file upload vulnerability, leading to RCE.
After the vendor released 8 versions of patch updates, I still discovered a vulnerability here.
And the exploitation method is different from CVE-2022-43192.
![Dedecms-v5.7.109-RCE-1.png](https://github.com/MentalityXt/Dedecms-v5.7.109-RCE/blob/main/Dedecms-v5.7.109-RCE-1.png)

## Vulnerability to reproduce
Log in to the backend of the website.

![Dedecms-v5.7.109-RCE-2.png](https://github.com/MentalityXt/Dedecms-v5.7.109-RCE/blob/main/Dedecms-v5.7.109-RCE-2.png)

Upload the file phpinfo.php, the content of the file is as follows:

![Dedecms-v5.7.109-RCE-3.png](https://github.com/MentalityXt/Dedecms-v5.7.109-RCE/blob/main/Dedecms-v5.7.109-RCE-3.png)

```
/*<?php
phpinfo();
?>*
```

Visit `phpinfo.php`：

![Dedecms-v5.7.109-RCE-4.png](https://github.com/MentalityXt/Dedecms-v5.7.109-RCE/blob/main/Dedecms-v5.7.109-RCE-4.png)

## Vulnerability Analysis

After adding comments using the /\*\*/ symbol in PHP, any code within the comment block will not be checked and can be easily uploaded. However, during actual access, the /\*\*/ comment symbols may not work as expected and the code within can still be executed.
