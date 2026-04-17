# Day 12 Lab - Mission Answers

## Part 1: Localhost vs Production

### Exercise 1.1: Anti-patterns found

1. API key hardcode trong code
2. Không có health check endpoint
3. Debug mode bật cứng
4. Không xử lý SIGTERM gracefully
5. Config không đến từ environment

### Exercise 1.3: Comparison table


| Feature      | Develop                 | Production                             | Why Important? |
| ------------ | ----------------------- | -------------------------------------- | -------------- |
| Config       | Hardcode trong code     | Đọc từ env vars     | Cùng một build có thể chạy dev/staging/prod; đổi cấu hình không cần sửa code. |
| Secrets      | `api_key = "sk-abc123"` | `os.getenv("OPENAI_API_KEY")` | Tránh lộ key trong repo; dễ rotate và phân quyền theo môi trường. |
| Port         | Cố định `8000`          | Từ `PORT` env var                      | Nền tảng cloud thường gán port động; app phải bind đúng port được cấp. |
| Health check | Không có                | `GET /health`                          | Load balancer/orchestrator biết instance còn sống và sẵn sàng nhận traffic. |
| Shutdown     | Tắt đột ngột            | Graceful — hoàn thành request hiện tại | Giảm lỗi khi deploy/scale-in; request đang xử lý không bị cắt đột ngột. |
| Logging      | `print()`               | Structured JSON logging                | Dễ parse, tìm kiếm và tích hợp với hệ thống log/monitoring tập trung. |


## Part 2: Docker

### Exercise 2.1: Dockerfile questions

1. Base image: [Your answer]
2. Working directory: [Your answer]

...

### Exercise 2.3: Image size comparison

- Develop: [X] MB
- Production: [Y] MB
- Difference: [Z]%

## Part 3: Cloud Deployment

### Exercise 3.1: Railway deployment

- URL: [https://your-app.railway.app](https://your-app.railway.app)
- Screenshot: [Link to screenshot in repo]

## Part 4: API Security

### Exercise 4.1-4.3: Test results

[Paste your test outputs]

### Exercise 4.4: Cost guard implementation

[Explain your approach]

## Part 5: Scaling & Reliability

### Exercise 5.1-5.5: Implementation notes

[Your explanations and test results]