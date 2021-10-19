# IAMList
# Google Cloud — IAM users extraction across all projects in a GCP org

Let’s see how to retrieve all the users list information from google cloud org in a cloud shell. To get the user list from a project , 
the below gcloud command is used

gcloud projects get-iam-policy $projectname

It displays the result in yaml format and what role they have, when the list is huge. [ You might have a different view on this :) ]

--members
  - rahulgupta@gmail.com
    role: roles/owner
    
Even if you are an org-admin, you wont be able to get the list of users for all projects in a single gcloud command . 
I think there might be a reason behind , on why google would want to display the user list structure in yaml format and 
limit the results to a single project, but wouldn’t be it nicer if it displays the user list in the below format, [ :) ]
so you can easily filter the roles and users in an excel sheet.

So we will go ahead and do that, I have given the steps involved in extraction as below,

1. Iterate through projects
2. use — format=”table(bindings)[0]” to extract the information in json format. (Note: I am comfortable with working on data in json format, 
if you think it is much more easier to retrieve the information in yaml format, you can also use that )
3. Clean the output from extra words and spaces (sed -e ‘s/^\w*\ *//’| tail -c +2)
4. pipe the output to a python file.
5. Use the json library to reformat the data and clean it further to display it in csv format.
That’s it !! done.

I have given the link below to my shell script and python script, Please feel free to use them. If you think there can be improvements made
to the script for a better version, you could do that too.
