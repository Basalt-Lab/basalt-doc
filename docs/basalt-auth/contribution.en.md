# **Contributing to Basalt Auth**

## **Introduction**

If you wish to contribute to **Basalt Auth**, it would be greatly appreciated!

The following steps will guide you through the contribution process, helping you understand how you can contribute to the project.

## **Contribution Process**

```mermaid
gitGraph:
options
{
    "nodeSpacing": 150,
    "nodeRadius": 10
}
end
commit
branch stage
checkout stage
commit
branch feature
checkout feature
commit
commit
checkout stage
merge feature
checkout main
merge stage
```

1. **Fork** the project  
   Start by creating a fork of the repository on GitHub. This will help you create your own copy of the project on your account, allowing you to make changes freely.
2. **Create** your feature branch (`git checkout -b feature/AmazingFeature`)  
   Create a new branch to work on your feature from the `stage` branch.
3. **Commit** your changes (`git commit -m 'feat: Add some AmazingFeature'`)  
   Once you have finished your modifications, you can commit them and prepare them for push.
   Please use [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/) for your commit messages, as this will automatically generate release notes.
4. **Push** to the branch (`git push origin feature/AmazingFeature`)  
   Once you have finished your modifications, you can push them to your fork.
5. Open a **Pull Request** to the `stage` branch  
   Once you have pushed your modifications to your fork, you can open a Pull Request to the `stage` branch of the main repository.
6. After your Pull Request is approved, your branch will be **merged** into `stage` and deleted.  
   Once your Pull Request has been approved, your branch will be merged into `stage` and deleted.

!!! warning "Note"
    Make sure to always update your local branch with the `stage` branch before starting to work on a new feature to ensure you are working with the latest version of the project.

## **Additional Notes**

Make sure to test all your modifications and add tests whenever possible.

Be open to feedback and suggestions on your pull request.

## **Acknowledgment**

Thank you sincerely for your interest in contributing to **Basalt Auth**. Your help is greatly appreciated and contributes to the improvement of the project for all users.
