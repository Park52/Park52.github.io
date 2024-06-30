---
layout: post
title: "C++ 최적화 - 4장 문자열 최적화"
date: 2024-06-30 12:00:00 +0000
categories: study
---

## 4장 문자열 최적화 요약

### 문자열 연산의 비용
문자열 연산은 많은 경우 매우 비싼 작업입니다. 문자열의 크기, 메모리 할당, 복사, 비교 등이 그 원인입니다. 따라서 문자열 최적화는 성능 향상을 위해 매우 중요합니다.

### 주요 최적화 기법

1. **문자열 리터럴 사용**
   - 문자열 리터럴을 사용하면 메모리 할당과 해제가 줄어들어 성능이 향상됩니다.
    ```cpp
    const char* str = "Hello, World!";
    ```
2. **불필요한 복사 피하기**
   - `std::string` 객체를 복사하면 전체 문자열이 복사되어 비효율적입니다. 이를 피하기 위해 참조를 사용하거나 `std::move`를 활용합니다.
    ```cpp
    void processString(const std::string& str);
    ```
3. **StringBuilder 패턴**
   - 많은 문자열을 연결할 때는 임시 객체가 많이 생성되지 않도록 StringBuilder와 같은 패턴을 사용하는 것이 좋습니다.
    ```cpp
    void example3() 
    {
        std::ostringstream builder;
        builder << "Hello" << ", " << "World!";
        std::string result = builder.str();
        std::cout << result << std::endl;
    }
    ```
4. **SBO (Small Buffer Optimization) 활용**
   - 많은 구현체에서 작은 문자열에 대해 동적 메모리 할당을 피하고 스택에 저장하는 최적화 기법을 사용합니다. `std::string`의 SBO를 이해하고 활용하는 것이 중요합니다.

5. **std::string_view 사용**
   - 문자열의 일부를 참조할 때 `std::string_view`를 사용하면 추가 복사 없이 효율적으로 문자열을 처리할 수 있습니다.
    ```cpp
    void processStringView(std::string_view sv) 
    {
        std::cout << sv << std::endl;
    }

    void example4() 
    {
        std::string myString = "Hello, World!";
        processStringView(myString);
    }
    ```
6. **메모리 풀 사용**
   - 많은 문자열 할당과 해제가 반복되는 경우 메모리 풀이 유용할 수 있습니다. 이는 메모리 단편화를 줄이고 성능을 향상시킵니다.
    ```cpp
    const char* str = "Hello, World!";
    ```

7. **코드 예제**
    - 문자열 리터럴과 불필요한 복사 피하기
    ```cpp
    void example1() 
    {
        const char* str = "Hello, World!";
        std::cout << str << std::endl;
    }

    void processString(const std::string& str) 
    {
        std::cout << str << std::endl;
    }

    void example2() 
    {
        std::string myString = "Hello, World!";
        processString(myString);
    }
    ```
