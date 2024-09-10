# Spring-Thymeleaf-CHEAT-SHEAT
cheat sheet for Spring Thymeleaf with practical examples, organized in a table format

<table>
  <thead>
    <tr>
      <th>Example</th>
      <th>Thymeleaf Code</th>
      <th>Spring Code</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Basic Button to Trigger API</td>
      <td>
        <pre><code>
<form th:action="@{/api/someEndpoint}" method="post">
  <button type="submit">Trigger API</button>
</form>
        </code></pre>
      </td>
      <td>
        <pre><code>
@PostMapping("/api/someEndpoint")
public String handlePost() {
    // Handle action
    return "redirect:/";
}
        </code></pre>
      </td>
    </tr>
    <tr>
      <td>2. Passing Data to API (GET Request)</td>
      <td>
        <pre><code>
<form th:action="@{/api/someEndpoint(id=${someId})}" method="get">
  <button type="submit">Get Data</button>
</form>
        </code></pre>
      </td>
      <td>
        <pre><code>
@GetMapping("/api/someEndpoint")
public String getData(@RequestParam("id") String id) {
    // Process data
    return "someView";
}
        </code></pre>
      </td>
    </tr>
    <tr>
      <td>3. Passing Data to API (POST Request)</td>
      <td>
        <pre><code>
<form th:action="@{/api/someEndpoint}" method="post">
  <input type="text" name="inputValue"/>
  <button type="submit">Submit</button>
</form>
        </code></pre>
      </td>
      <td>
        <pre><code>
@PostMapping("/api/someEndpoint")
public String handlePost(@RequestParam("inputValue") String inputValue) {
    // Process input
    return "someView";
}
        </code></pre>
      </td>
    </tr>
    <tr>
      <td>4. Loading List of Items from API</td>
      <td>
        <pre><code>
<ul>
  <li th:each="item : ${itemsList}" th:text="${item.name}"></li>
</ul>
        </code></pre>
      </td>
      <td>
        <pre><code>
@GetMapping("/items")
public String getItems(Model model) {
    List&lt;Item&gt; itemsList = itemService.getAllItems();
    model.addAttribute("itemsList", itemsList);
    return "itemsView";
}
        </code></pre>
      </td>
    </tr>
    <tr>
      <td>5. Conditionals (If-Else)</td>
      <td>
        <pre><code>
<div th:if="${isLoggedIn}">Welcome, User!</div>
<div th:unless="${isLoggedIn}">Please log in.</div>
        </code></pre>
      </td>
      <td>
        <pre><code>
@GetMapping("/dashboard")
public String showDashboard(Model model) {
    model.addAttribute("isLoggedIn", authService.isLoggedIn());
    return "dashboardView";
}
        </code></pre>
      </td>
    </tr>
    <!-- Add more rows as needed -->
  </tbody>
</table>
