The programming language is JavaScript.
All the scripts use pm (Postman) library and test() method.
Assertions use Chai library.

The tests scripts for the API endpoint:
----------------------------------------------------------------------------------------------------------------
pm.test('Status code',function (){
    pm.expect(pm.response).to.have.status(200);
});

pm.test('Response should be in json format', () => {
    pm.expect(pm.response).to.be.json;
});

pm.test("Response time is less than 200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(200);
});

pm.test("Response cookies should not contain 'session_token'", function () {
    pm.expect(pm.response.cookies.has("session_token")).to.be.false;
}); // endpoint www.thecocktaildb.com/api/json/v1/1/lookup.php?i={{random}} does not contain any cookies

pm.test("Response 'headers' with key 'Content-Type' should contain value 'application/json'", () => {
    pm.expect(pm.response.headers.get("Content-Type")).to.contain("application/json");
});
---------------------------------------------------------------------------------------------------------------
I also attached a screen shot for the Test Results.
