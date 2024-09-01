# Streamlit に認証機能をつける

[mkhorasani/Streamlit-Authenticator: A secure authentication module to manage user access in a Streamlit application. (github.com)](https://github.com/mkhorasani/Streamlit-Authenticator)

# Requirement

- Python 3.11
- poetry 環境

```shell
poetry install
```

- 以下の VSCode 拡張機能を入れることを推奨

  - Black Formatter
  - isort

# Usage

config.yaml にはサンプルのユーザー情報が入っているので、必要に応じて書き換える。

以下のコマンドで実行

```bash
poetry shell
streamlit run src/app.py
```

# Caution!

## 0.3.3 だと auto_hash は機能しない

[Invalid salt from 0.3.3 · Issue #186 · mkhorasani/Streamlit-Authenticator (github.com)](https://github.com/mkhorasani/Streamlit-Authenticator/issues/186)

に記載の通り、0.3.3 だと auto_hash が機能しないので

```python

stauth.Hasher.hash_passwords(config["credentials"]),

```

のように事前に hash 化する必要あり。

## 前回の Cookie が残ったままだとうまく動かないことも

```
streamlit_authenticator.utilities.exceptions.LoginError: User not authorized
```

で躓いたら、Cookie を削除してみると解消される可能性あり。
