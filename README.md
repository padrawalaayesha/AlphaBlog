# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
 <table>
    <thead>
      <tr>
        <th>Title</th>
        <th>Description</th>
        <th colspan = "3">Actions</th>
      </tr>
    </thead>
    <tbody><% @articles.each do |article|%>
        <tr>
          <td><%= article.title %></td>
          <td><%=article.description %></td>
          <td><%=link_to 'Show', article_path(article)%></td>
          <td><%= link_to 'Edit',edit_article_path(article)%></td>
          <td><%=link_to 'Delete', article_path(article), method: :delete, data: {confirm: "Are you sure you want to delete ?"}%></td>
        </tr>
        <% end%>
    </tbody>
  </table>
  <p>
  <%=link_to'Create a new article', new_article_path%>
  </p>
  <%if @article.errors.any?%>
  <div class="alert alert-danger alert-dismissible fade show" role="alert">
    <h4 class="alert-heading">The following errors prevented the creation of article</h4>
    <ul>
    <%@article.errors.full_messages.each do |msg|%>
        <li><%=msg%></li>
    <%end%>
   </ul>
    <button type="button" class="close" data-dismiss="alert" aria-label="Close">
       <span aria-hidden="true">&times;</span>
    </button>
 </div>
<%end%>
<h1>Showing article details </h1>
<p><strong>Title: </strong><%= @article.title %></p>
<p><strong>Description: </strong><%= @article.description %></p>
<p>
  <%=link_to'Edit',edit_article_path(@article)%> |
  <%=link_to'Delete', article_path(@article), method: :delete ,data: {confirm: "Are you sure you want to delete ?"}%> |
  <%=link_to'Return to article listing', articles_path%>
</p>
<li class="nav-item">
              <%=link_to'Articles',articles_path, class:"nav-link"%>
              </li>
               <li class="nav-item">
                  <%=link_to current_user.username ,user_path(current_user), class:"nav-link "%>
                 </li>
  test "should create category" do
    assert_difference('Category.count') do
      post categories_url, params: { category: {  } }
    end

    assert_redirected_to category_url(Category.last)
  end
   test "should get edit" do
    get edit_category_url(@category)
    assert_response :success
  end
    test "should update category" do
    patch category_url(@category), params: { category: {  } }
    assert_redirected_to category_url(@category)
  end

  test "should destroy category" do
    assert_difference('Category.count', -1) do
      delete category_url(@category)
    end

    assert_redirected_to categories_url
  end