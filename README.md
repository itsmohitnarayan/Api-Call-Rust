# 🚀 Rust Web API Client Demo

A simple Rust program demonstrating how to make an HTTP request to the GitHub API to retrieve stargazers for a repository. 🦀

## 📖 Overview

This project uses the `reqwest` and `serde` crates to interact with the GitHub API and deserialize the JSON response into a vector of `User` structs.

## 🛠️ Usage

To run the program, make sure you have Rust installed. Then, clone the repository and execute the following commands:

```bash
cargo build
cargo run
```

This will print the list of stargazers for the specified GitHub repository.

## 🧑‍💻 Code Example

```rust
#[tokio::main]
async fn main() -> Result<(), Error> {
    let owner = "rust-lang-nursery";
    let repo = "rust-cookbook";

    let request_url = format!("https://api.github.com/repos/{}/{}/stargazers", owner, repo);
    println!("{}", request_url);

    let client = reqwest::Client::new();
    let response = client
        .get(&request_url)
        .header(USER_AGENT, "rust web-api-client demo")
        .send()
        .await?;

    let users: Vec<User> = response.json().await?;
    println!("{:?}", users);

    Ok(())
}
```

## 🚨 Note

- This project is for educational purposes and serves as a basic example of making web API calls in Rust.
- Ensure you have a stable internet connection to fetch data from the GitHub API.
```
Feel free to explore and modify the code as needed for your projects! Happy coding! 🎉
```

-----------------------------------------------------------------------------------------------------------------------
