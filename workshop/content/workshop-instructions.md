The workshop dashboard consists of the workshop instructions on the left hand side, and a pair of terminals on the right hand side. All interaction with the Kubernetes cluster performed in the workshops uses the ``kubectl`` command line tool. To find out the version of Kubernetes being used, you can run:

```execute
kubectl version
```

Did you type the command in yourself? If you did, click on the command instead and you will find that it is executed for you.

You can click on any command in the workshop instructions which has the <span class="fas fa-running"></span> icon shown to the right of it, and it will be copied to the appropriate interactive terminal and run. If you would rather make a copy of the command so you can paste it to another window, hold down the shift key when you click on the command.

Commands or other content which you need to enter, may also be annotated with either the <span class="fas fa-copy"></span> or <span class="fas fa-user-edit"></span> icons. When you click on either of these, the content will be copied into your paste buffer ready to paste into the appropriate window. When that content needs to be modified before it is used, the second of these two icons will be that which is used.

Although ``kubectl`` will be used to execute commands against the Kubernetes cluster, the Kubernetes dashboard is also provided for exploring the cluster. This can be found by clicking on the **Console** tab.

If you want to end the workshop early, you can select **Restart Session** from the drop down menu on the right hand side.
