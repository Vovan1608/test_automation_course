Requirement for register(login, password) method:

1. If user with this login doesn't exist and password is valid method should return some random string
2. If user with this login exist method throws EntityAlreadyExistsException
3. If login is empty or equal to null method throws IllegalArgumentException with message "The login can't be blank"
4. If password doesn't contain at least one number, at least one letter and at least one special characters and at least 8 characters method throws IllegalArgumentException with appropriate message

Task:

Create at least 8 unit tests for this method according to these requirements. Some tests should be failed due to incorrect implementation of this method.

```java
package org.example;

import org.junit.jupiter.api.BeforeAll;
import org.junit.jupiter.api.DisplayName;
import org.junit.jupiter.api.Test;

import java.util.HashMap;
import java.util.Map;

import static org.junit.jupiter.api.Assertions.*;
import static org.junit.jupiter.api.Assertions.assertThrows;

class AuthServiceTest {

    private static AuthService authService;

    private static final String VALID_PASSWORD = "Pas11_0A";
    private static final String PASSWORD_WITHOUT_NUMBER = "Qwerty@#$";
    private static final String  PASSWORD_WITHOUT_LETTER = "123456%^&";
    private static final String  PASSWORD_WITHOUT_SPEC_CHAR = "Qwert1234";
    private static final String  PASSWORD_LENGTH_LESS_EIGHT_CHAR = "Qw#t12";

    private static final String  PASSWORD_WITHOUT_UPPER_CHAR = "qwert#t12";

    private static final String  PASSWORD_WITHOUT_LOWER_CHAR = "QWERT#t12";

    @BeforeAll
    static void beforeAll() {
        Map<String, String> users = new HashMap<>(Map.of("user", "password1", "user2", "password1", "user3", "password2", "us", "pass"));
        authService = new AuthService(users);
    }

    @Test
    @DisplayName("When user with non-existing login and valid password registered then returns non-empty string")
    void registerUser() {
        String result = authService.registration("Other user", "qQ1!Qq!1");
        assertFalse(result.isEmpty(), "Register user method should return some non-empty string");
    }

    @Test
    @DisplayName("When user with some login already exists in store then EntityAlreadyExistsException is generated")
    void tryRegisterUserThatAlreadyExist() {
        EntityAlreadyExistsException thrown = assertThrows(EntityAlreadyExistsException.class, () -> {
            authService.registration("user", VALID_PASSWORD);
        });
        assertEquals("User with such login already exists", thrown.getMessage());
    }

    @Test
    @DisplayName("If login is empty method throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithEmptyLogin() {
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("", VALID_PASSWORD);
        });
        assertEquals("The login can`t be blank", thrown.getMessage());
    }

    @Test
    @DisplayName("If login is null method throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithNullLogin() {
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration(null, VALID_PASSWORD);
        });
        assertEquals("The login can`t be blank", thrown.getMessage());
    }

    @Test
    @DisplayName("If password doesn't contain at least one number throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithPassWithoutNum() {
        String mess = "The password must be a combination of numbers, upper and lower letters, and special characters and at least 8 characters";
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("user", PASSWORD_WITHOUT_NUMBER);
        });
        assertEquals(mess, thrown.getMessage());
    }

    @Test
    @DisplayName("If password doesn't contain at least one letter throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithPassWithoutLetter() {
        String mess = "The password must be a combination of numbers, upper and lower letters, and special characters and at least 8 characters";
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("user", PASSWORD_WITHOUT_LETTER);
        });
        assertEquals(mess, thrown.getMessage());
    }

    @Test
    @DisplayName("If password doesn't contain at least one special characters throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithPassWithoutSpecChar() {
        String mess = "The password must be a combination of numbers, upper and lower letters, and special characters and at least 8 characters";
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("user", PASSWORD_WITHOUT_SPEC_CHAR);
        });
        assertEquals(mess, thrown.getMessage());
    }

    @Test
    @DisplayName("If password doesn't contain at least 8 characters throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithLengthLessThenEight() {
        String mess = "The password must be a combination of numbers, upper and lower letters, and special characters and at least 8 characters";
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("user", PASSWORD_LENGTH_LESS_EIGHT_CHAR);
        });
        assertEquals(mess, thrown.getMessage());
    }

    @Test
    @DisplayName("If password doesn't contain upper letters throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithoutUpperLetters() {
        String mess = "The password must be a combination of numbers, upper and lower letters, and special characters and at least 8 characters";
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("user", PASSWORD_WITHOUT_UPPER_CHAR);
        });
        assertEquals(mess, thrown.getMessage());
    }

    @Test
    @DisplayName("If password doesn't contain lower letters throws IllegalArgumentException with message 'The login can`t be blank'")
    void tryRegisterUserWithoutLowerLetters() {
        String mess = "The password must be a combination of numbers, upper and lower letters, and special characters and at least 8 characters";
        IllegalArgumentException thrown = assertThrows(IllegalArgumentException.class, () -> {
            authService.registration("user", PASSWORD_WITHOUT_LOWER_CHAR);
        });
        assertEquals(mess, thrown.getMessage());
    }
}
```
