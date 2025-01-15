# Pull Request 템플릿

---

## **Pull Request 란?**
Pull Request(PR)는 **코드 변경 상황을 리뷰하고 병합**하기 위해 다른 개발자에게 요청을 보내는 기능입니다.  
팀원들과 협업하는 GitHub, GitLab과 같은 플랫폼에서 사용되며, 변경 상황을 체계적으로 검토하고 관리할 수 있습니다.

---

## **예시**

### **XX 사이트의 예시**  
- **간단한 제목**: `Fix: 로그인 오류 수정`  
- **설명**:  
  ```
  - 로그인 시 비밀번호 검증 로직이 잘못되어 수정했습니다.
  - 관련된 이슈 번호: #123
  - 테스트 추가: 성공적인 로그인 확인
  ```

---

### **OO 사이트의 예시**  
- **제목**: `Feature: 새로운 API 엔드포인트 추가`  
- **설명**:  
  ```
  - 추가된 기능: /api/v1/products 엔드포인트 구현
  - 세부사항:
      - GET /api/v1/products: 제품 목록 반환
  - 코드 리뷰가 필요한 파일: 
      - ProductController.java
      - ProductService.java
  ```

---

## **Repository 에 추가하는 방법**

1. **템플릿 파일 생성**  
   - 리포지톱 룰트 디렉토리 또는 `.github/` 폴더 안에 `PULL_REQUEST_TEMPLATE.md` 파일을 생성합니다.  
   
   **예시 경로**:  
   ```
   .github/PULL_REQUEST_TEMPLATE.md
   ```

2. **템플릿 내용 작성**  
   위에 작성된 템플릿 내용을 복사해서 붙여넣습니다.

3. **컨미트 및 푸시**  
   ```bash
   git add .github/PULL_REQUEST_TEMPLATE.md
   git commit -m "Add Pull Request Template"
   git push origin main
   ```

---

## **기타 예시**

```yaml
foo:
  bar:
    - baz
```

---

