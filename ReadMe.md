# 2ristPanel B2C RESTful API

 <h3><a target="_blank" href="https://www.aparat.com/v/I5EP3">ویدیو آموزشی به زبان فارسی</a></h3>
<div>
    <p>The 2ristPanel API allows you to programmatically access to your account with ease.</p>
    <h1 id="overview">Overview</h1>
    <ol>
        <li>
            <p>You need a valid <a href="#authentication">Bearer jwt Token</a> to send requests to the API endpoints. You can get your public and private key from the <a target="_blank" href="https://app.2ristpanel.com/Main/Panel/Profile/ApiManagements">Api Key Managements</a>.</p>
        </li>
        <li>
            <p>The API has an access <a href="#time-limits">Time Limit</a> applied to it.</p>
        </li>
        <li>
            <p>The 2ristPanel API will only respond to secured communication done over HTTPS. HTTP requests will be sent a <code>301</code> redirect to corresponding HTTPS resources.</p>
        </li>
        <li>
            <p>The API calls will respond with appropriate <a href="https://en.wikipedia.org/wiki/List_of_HTTP_status_codes">HTTP status codes</a> for all requests. Within 2ristPanel Client, when a response is received, the status code is highlighted and is accompanied by a help text that indicates the possible meaning of the response code. A <code>200 OK</code> indicates all went well, while <code>4XX</code> or <code>5XX</code> response codes indicate an error from the requesting client or our API servers respectively.</p>
        </li>
    </ol>
    <h1 id="authentication">Authentication</h1>
    <p>An Bearer jwt Token is required to be sent as part of every request to the 2ristPanel API, in the form of an <code>Authorization : Bearer yJhbIkpXCJ9.eyJVc2VyS....... </code> request header.</p>
    <blockquote>
        <p>If you do not have an API Key, you can easily generate one by heading over to the <a href="https://app.2ristpanel.com/Main/Panel/Profile/ApiManagements">Api Key Managements</a></p>
    </blockquote>
    <p>An API Key tells our API server that the request it received came from you. Everything that you have access to in 2ristPanel is accessible with an API Key that is generated by you.<br />
    you can genrate new token via <a href="#operations-API-post_v1_API_GenerateNewToken">GenerateNewToken</a> Method
    </p>
    <h2 id="api-key-related-error-response">API Key related error response</h2>
    <p>If an API Key is missing, malformed, or invalid, you will receive a <code>401 Unauthorised</code> response code and the following JSON response:</p>
    <pre class="  language-undefined"><code class="language-undefined">
    {
    "message": "The Authorization Token is missing Or does not send in the header.",
    "title": "SessionRevokingMessage",
    "notificationViewType": 1,
    "notificationType": 2,
    "state": false
    }
</code></pre>
    <h1 id="time-limits">Time Limits</h1>
    <p>After receiving a new token you will have <code>3 minutes</code> to use the token. After the specified time the token will be expired and you must create a new token</p>
    <h1 id="support">Support</h1>
    <p>For help regarding accessing the 2ristPanel API, feel free to drop a ticket at our <a target="_blank" href="https://support.2ristpanel.ir">Support</a> system.</p>
    <p>In the event you receive a <code>503</code> response from our servers, it implies that we have hit an unexpected spike in API access traffic and would usually be operational within the next 5 minutes. If the outage persists, or your receive any other form of <code>5XX</code> error, kindly let us know.</p>

</div>

 <h1 id="terms-of-use">API Base Url</h1>

<table>
   <thead>
        <th>API Type</th>
        <th>API URL</th>
   </thead>
   <tbody>
   <tr>
       <td>Test And Demo</td>
       <td>https://beta-api.2ristpanel.com</td>
    </tr>
       <tr>
       <td>Production</td>
       <td>https://api.2ristpanel.com</td>
    </tr>
   </tbody>
</table>

To test the API, create the following values as a variable in Postman
Note that these values are only valid in the demo version

<table>
   <thead>
        <th>VARIABLE</th>
        <th>INITIAL VALUE</th>
   </thead>
   <tbody>
   <tr>
       <td>baseUrl</td>
       <td>https://beta-api.2ristpanel.com</td>
    </tr>
       <tr>
       <td>publicKey</td>
       <td>28GW9JEROEY5BDN</td>
    </tr>
       <tr>
       <td>privateKey</td>
       <td>8059c822-4205-472d-bc40-c5e8669af403</td>
    </tr>
       <tr>
       <td>authorization</td>
       <td></td>
    </tr>
   </tbody>
</table>

Result of Response 200 can be an object with the requested content or an error.
You can see the list of known errors below

<table>
   <thead>
        <th>Code</th>
        <th>Description</th>
        <th>توضیحات</th>
   </thead>
   <tbody>
   <tr>
       <td>100</td>
       <td>There is a problem with one of the Unique IDs sent. The name of the ID is mentioned in the error</td>
       <td>ایرادی در یکی از آیدی های یونیک ارسالی وجود دارد. نام آی دی در ارور ذکر شده است</td>
    </tr>
    <tr>
       <td>101</td>
       <td>The requested number of one of the tickets is more than the inventory. The name of the requested ticket and the remaining number are mentioned in the error.</td>
       <td>تعداد درخواستی یکی از تیکت ها بیشتر از  موجودی میباشد نام تیکت درخواستی و تعداد باقی مانده در ارور ذکر شده است</td>
    </tr>
    <tr>
       <td>102</td>
       <td>The requested service requires the names of the passengers. Please send the relevant field in a completed form. The service name is listed in the error</td>
       <td>برنامه درخواستی نیاز به اسامی مسافران دارد لطفا فیلد مربوطه را به صورت تکمیل شده ارسال نمایید نام برنامه در ارور ذکر شده است</td>
    </tr>
    <tr>
       <td>103</td>
        <td>The requested service requires the names of the passengers along with the national code or passport number and its type. Please send the relevant field in a completed form. The service name is listed in the error</td>
       <td>سرویس درخواستی، نیاز به اسامی مسافران به همراه کد ملی یا شماره پاسپورت و نوع آن دارد لطفا فیلد مربوطه را به صورت تکمیل شده ارسال نمایید. نام سرویس در ارور ذکر شده است
       </td>
    </tr>
    <tr>
       <td>104</td>
       <td>There is a problem with opening the cash desk automatically.
           Please make sure that in the panel settings, the cash desk closure is activated automatically, and if         you have the open cash desk, close it and send the request again.
       </td>
        <td>ایرادی در باز نمودن صندوق فروش به صورت اتوماتیک به وجود آمده است.
         لطفا اطمینان حاصل نمایید که در تنظیمات پنل، بسته شدن صندوق فروش به صورت اتوماتیک فعال است و در صورتی که صندوق باز دارید آن را بسته و مجددا درخواست را ارسال نمایید.
        </td>
    </tr>
    <tr>
       <td>105</td>
       <td>The temporary reservation reference has a problem, has been canceled or has been used before, please note that temporary reservations only take up to 30 minutes, after which your reference will be invalidated.</td>
       <td>رفرنس رزرو موقت ایراد دارد، باطل شده و یا قبلا استفاده شده است است لطفا توجه داشته باشید که رزرو های موقت فقط تا 30 دقیقه زمان دارند و بعد از آن رفرنس شما باطل میشود  </td>
    </tr>
    <tr>
       <td>106</td>
       <td>You are allowed to book 7 items at a time and 15 tickets per item at each request. This error indicates that you have requested more than the specified number.</td>
       <td>شما در هر درخواست اجازه رزرو موقت 7 آیتم و در هر آیتم 15 بلیط را دارا هستید این ارور نشان دهنده این است که شما بیش از تعداد ذکر شده درخواست داده اید</td>
    </tr>
    <tr>
       <td>107</td>
       <td>Booking time is over</td>
       <td>زمان رزرو موقت به پایان رسیده است</td>
    </tr>
    <tr>
       <td>108</td>
       <td>The problem is with the information sent to the passenger list. Please check the manifest and send data again</td>
       <td>ایراد مربوط به اطلاعات ارسالی در لیست مسافرین است. لطفا لیست را بررسی و مجددا ارسال نمایید</td>
    </tr>
    <tr>
       <td>109</td>
       <td>Your purchase credit on the panel is over or less than allowed. Please check and charge your credit</td>
       <td>اعتبار خرید شما در پنل به اتمام رسیده یا کمتر از حد مجاز میباشد لطفا اعتبار خود را بررسی و شارژ نمایید</td>
    </tr>
        <tr>
       <td>110</td>
       <td>This license Is not valid on this Service or not valid at all</td>
       <td>مجوز ارسالی برای این برنامه اعتبار ندارد</td>
    </tr>
   </tbody>
</table>

 <h1 id="terms-of-use">Developer And Ownership Details</h1>

Licenced To
<a href="http://toptis.ir/"  target="_blank">TopTis</a>
-
<a href="http://ttgroup.ir/"  target="_blank">TopTours</a>
Developed By:
<a href="https://pooriashariatzadeh.com" target="_blank">Pooria Shariatzadeh</a>

## Version: 1.0

### /API/GenerateNewToken

#### POST
##### Summary

GenerateNewToken

##### Parameters

| Name  | Description | Required | Schema |
| ----  | ----------- | -------- | ---- |
| publicKey  | Created in Panel | Yes | string |
| privateKey  | Created in Panel | Yes | string |
##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/GetActiveDestinations

#### GET
##### Summary

GetActiveDestinations

##### Description

You can call this method to get a list of cities that have an active event
Note that this list consists of two record models
Tourist cities have a separate record, often in the form of "state / city" and other cities that are classified as state.

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |
<code class="body-block is-highlighted language-javascript">
{
 "authorization": "Bearer yJhbIkpXCJ9.eyJVc2VyS......."
}

</code>
### /B2C/Booking/GetActiveLicences

#### GET
##### Summary

GetActiveLicences

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/GetWalletsBalance

#### GET
##### Summary

GetWalletsBalance

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/GetAllServicesAsync

#### GET
##### Summary

GetAllServicesAsync

##### Description

<h1>EventType</h1>

<table>

   <thead>

        <th>Value</th>

        <th>Title (english)</th>

        <th>Title (persian)</th>

   </thead>

   <tbody>

   <tr>

       <td>1</td>

       <td>Tourism Fun</td>

       <td>برنامه های تفریحی </td>

    </tr>

      <tr>

       <td>2</td>

       <td>Seated Salon Events</td>

       <td>برنامه هایی با قابلیت رزرو صندلی</td>

    </tr>

   </tbody>

</table>

<h1>EventCategory</h1>

<table>

   <thead>

        <th>Value</th>

        <th>Title (english)</th>

        <th>Title (persian)</th>

   </thead>

   <tbody>

   <tr>

       <td>1</td>

       <td>Parks And Amusements</td>

       <td> </td>

    </tr>

   <tr>

       <td>2</td>

       <td>Restaurants</td>

       <td> </td>

    </tr>

       <tr>

       <td>3</td>

       <td>Rest And Relaxation</td>

       <td> </td>

    </tr>

       <tr>

       <td>4</td>

       <td>Seaside Club</td>

       <td> </td>

    </tr>

       <tr>

       <td>5</td>

       <td>Tours And Excursions</td>

       <td> </td>

    </tr>

       <tr>

       <td>6</td>

       <td>Night Shows And Concerts</td>

       <td> </td>

    </tr>

       <tr>

       <td>7</td>

       <td>Yachts</td>

       <td> </td>

    </tr>

       <tr>

       <td>8</td>

       <td>Museums and Historic Attractions</td>

       <td> </td>

    </tr>

       <tr>

       <td>9</td>

       <td>Discount Coupon</td>

       <td> </td>

    </tr>

       <tr>

       <td>10</td>

       <td>Cafe Restaurant</td>

       <td> </td>

    </tr>

       <tr>

       <td>11</td>

       <td>Entertainment Club</td>

       <td> </td>

    </tr>

   </tbody>

</table>

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| StateCode | query | int (ضروری نیست) | Yes | string |
| CityCode | query | int (ضروری نیست) | Yes | string |
| HasActiveSans | query | bool (ضروری نیست) | Yes | boolean |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/GetServiceAsync

#### GET
##### Summary

GetServiceAsync

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| ServiceUniqueId | query | GUID (ضروری است) | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/GetAvailableSansAsync

#### GET
##### Summary

GetAvailableSansAsync

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| ServiceUniqueId | query | GUID (ضروری است) | Yes | string |
| LicenseUniqueId | query | GUID (ضروری است) | Yes | string |
| PersianDate | query | تاریخ هجری شمسی با فرمت 1399/01/01 در صورت عدم ارسال لیست تمامی سانس های فعال ارسال میگردد  | Yes | string |
| TicketTypeUniqueIds | query | آرایه ای از یونیک آیدی های نوع بلیط که توسط ' , ' از یک دیگرجدا شده هستند (غیر ضروری) 141b8a2b-8458-46ec-b64e-c0a086c39513,8ac9e825-ba8c-4cf9-ac47-a7cff72dcbd5 | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/CheckItemAvailabilityAsync

#### GET
##### Summary

CheckItemAvailabilityAsync

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| TicketTypeUniqueId | query | GUID (ضروری است) | Yes | string |
| SansUniqueId | query | GUID (ضروری است) | Yes | string |
| LicenseUniqueId | query | GUID (ضروری است) | Yes | string |
| Number | query | int (تعداد بلیط درخواستی (ضروری است) | Yes | integer |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/TempBookingAsync

#### POST
##### Summary

TempBookingAsync

##### Description

<ul>
<li>
<p><code>fullName</code> and <code>mobilePhone</code> are required<p/>
</li>

<li>
<p>In the <code>bookItems</code> array, you can send a maximum of <strong>7</strong> Sans, and in each Sans, you can send a maximum of 15 tickets. If the number of tickets or the number of Sans is more than the allowed limit, your temporary reservation will not be made.</p>
</li>

<li>
<p>Please note that if the value of <code>isManifestNeeded</code> in the <code>GetServiceAsync</code> method is equal to <code>true</code>, you must send the list of names of the passengers in the <code>manifest</code> field equal to the number of requested tickets.<br />Also, if the field <code>isManifestUniqueNumberNeeded</code> is equal to <code>true</code>, the two fields <code>uniqueNumberType</code> and <code>uniqueNumber</code> should be sent.<br />The value of <code>uniqueNumberType</code>, if the type is <code>uniqueNumber</code>, is the national code of Iran 1 and the passport number 2 should be sent.</p>

The structure of the <code>manifest</code> array should be as follows
<pre class="body-block click-to-expand-wrapper is-snippet-wrapper language-javascript" data-title="BODY Raw">
<code class="body-block is-highlighted language-javascript">
"manifest": [{

    "fullName": "پوریا شریعت زاده",

    "uniqueNumber": "0921557555",

    "uniqueNumberType": 1

    },

    {

    "fullName": "Tom Holland",

    "uniqueNumber": "H56245856",

    "uniqueNumberType": 2

    }]

</code>
</pre>
</li>
</ul>

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/CancelingTempBookingAsync

#### DELETE
##### Summary

CancelingTempBookingAsync

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| TempBookingReference | query |  | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/FinalizingBookingAsync

#### GET
##### Summary

FinalizingBookingAsync

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| TempBookingReference | query | رفرنش 15 حرفی که از متد تمپ بوکینگ دریافت کرده اید string | Yes | string |
| DiscountAmount | query | مبلغ تخفیف جهت ثبت در صندوق فروش روزانه <double> | Yes | integer |
| SendSMS | query | آیا مایل به ارسال لینک تیکت ها  با پیامک به مشتری هستید ؟  | Yes | boolean |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/GetSalonViewOnlyUrl

#### GET
##### Summary

GetSalonViewOnlyUrl

##### Description

خروجی این متد یک لینک است که میتوانید به صورت آیفریم در سایت خود قرار دهید
<br>
لطفا توجه داشته باشید که این لینک فقط جهت مشاهده سالن و صندلی های قابل رزرو میباشد و قابلیت رزرو را ندارد

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |
| LicenseUniqueId | query | GUID (ضروری است) | Yes | string |
| SansUniqueId | query | GUID (ضروری است) | Yes | string |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### /B2C/Booking/CreateTempShoppingCartForSalonSeatReservation

#### POST
##### Summary

CreateTempShoppingCartForSalonSeatReservation

##### Description

لطفا توجه داشته باشید که از این متد فقط در جهت باز نمودن یک سبد خرید موقط برای برنامه هایی که قابلیت رزرو با صندلی را دارا هستند استفاده نمایید
<br>
پس از فراخوانی این متد خروجی به شما تمامی اطلاعات مورد نیاز (لینک تمایش سالن و کد فاینال کردن سبد خرید) را برای شما ارسال خواهد کرد
<br>
در نهایت با متد FinalizingBookingAsync سبد خرید موقت خود را فاینال نمایید

##### Parameters

| Name | Located in | Description | Required | Schema |
| ---- | ---------- | ----------- | -------- | ---- |

##### Responses

| Code | Description |
| ---- | ----------- |
| 200 |  |

### Models

#### GenerateNewTokenRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| publicKey | string |  | Yes |
| privateKey | string |  | Yes |

**Example**
<pre>{
  "publicKey": "<string>",
  "privateKey": "<string>"
}</pre>

#### Success

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| authorization | string |  | Yes |

**Example**
<pre>{
  "authorization": "<string>"
}</pre>

#### GetActiveDestination

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| title | string |  | Yes |
| titleNative | string |  | Yes |
| stateCode | integer |  | Yes |
| cityCode | integer |  | Yes |
| activityCount | integer |  | Yes |

**Example**
<pre>{
  "title": "Hormozgan / Kish",
  "titleNative": "هرمزگان / کیش",
  "stateCode": 20,
  "cityCode": 351,
  "activityCount": 59
}</pre>

#### GetActiveLicence

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| location | string |  | Yes |
| locationNative | string |  | Yes |
| stateCode | integer |  | Yes |
| cityCode | integer |  | Yes |
| availableEventCount | integer |  | Yes |
| licenceUniqueId | string |  | Yes |
| issuedBy | string |  | Yes |
| type | string |  | Yes |

**Example**
<pre>{
  "location": "Hormozgan / Kish",
  "locationNative": "هرمزگان / کیش",
  "stateCode": 20,
  "cityCode": 351,
  "availableEventCount": 58,
  "licenceUniqueId": "7b397343-9f4c-48b4-8a06-39a2803ecef6",
  "issuedBy": "System",
  "type": "Agency"
}</pre>

#### GetWalletsBalance

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| owner | string |  | Yes |
| amount | integer |  | Yes |

**Example**
<pre>{
  "owner": "System",
  "amount": 5816000
}</pre>

#### GetServiceAsync

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| serviceUniqueId | string |  | Yes |
| eventCategory | string |  | Yes |
| title | string |  | Yes |
| description | string |  | Yes |
| rules | string |  | Yes |
| coverImage | string |  | Yes |
| gallery | [ string ] |  | Yes |
| isManifestNeeded | boolean |  | Yes |
| isManifestUniqueNumberNeeded | boolean |  | Yes |
| licences | [ object ] |  | Yes |
| ticketTypes | [ object ] |  | Yes |
| hasActiveSans | boolean |  | Yes |

**Example**
<pre>{
  "serviceUniqueId": "8eb48025-cb62-437f-8a64-79fdb5f9927b",
  "eventCategory": "SeasideClub",
  "title": "کلوپ تفریحات دریایی نگین",
  "description": "آدرس: نوارساحل جنب مرکز تفریحات دریایی پشت مسجد امیر (ع)     شماره رزرواسیون :09347694166 \r\nهمراه داشتن حوله , دمپایی, تیشرت و یک دست لباس اضافه الزامی میباشد.*لطفا قبل از عزيمت با تلفن هاي کلوپ تماس حاصل نموده و ساعت حضور دقيق را دريافت نمائيد*.بليت شامل قوانين چارتر بوده و غير قابل استرداد ميباشدوهمراه داشتن بليت جهت پذیرش الزامي است.*اعتبار استفاده از بليت،طبق تاريخ درج شده بر روي بليت بوده و در صورت انقضا،بليت فاقد اعتبار است.*حضور شما 30 دقيقه قبل ازانجام خدمات در محل الزامي بوده واز آوردن اشياء زينتي و قيمتي خودداري فرمائيد*",
  "rules": ".پوشيدن جليقه نجات در کلوپ هاي دريايي الزامي وافراد داراي ناراحتي قلبي تنفسي و بانوان باردار اجازه استفاده از غواصي وفلای برد را ندارند.سرويس دهي شاتل از 2الي4 نفر و بانانا از 4الي8نفر انجام مي شود و مدت زمان استفاده از شاتل و بنانا  ۱۵ دقيقه مي باشد و افراد 6سال به بالا با رضايت والدين اجازه استفاده از خدمات را دارند.حداکثر ارتفاع مجاز پاراسل ۷۰ متر از سطح آب با طول طناب ۱۵۰ متر است و بابت مسافر همراه در قايق پاراسل مبلغ   ۲۵,۰۰۰ هزار تومان دريافت مي گردد ودرضمن پاراسل براي افراد ۱۸ سال به بالا امکان پذير است و مدت زمان استفاده از پاراسل ۶ دقيقه مي باشدتهيه بليط براي کودکان۱۰سال به بالا الزامي بوده و زير ۱۰ سال امکان ارائه سرويس  فلای بورد  نداردمدت زمان برنامه  فلای بورد  ۲۰  دقيقه و حضور شما زير آب برای غواصی ۱۵ دقيقه مي باشد",
  "coverImage": "https://app.2ristpanel.com/files/attachments/6b7fd6e5-7fc0-4384-bccc-e7c74f62ee39.jpg",
  "gallery": [],
  "isManifestNeeded": false,
  "isManifestUniqueNumberNeeded": false,
  "licences": [
    {
      "licenceUniqueId": "d6e98a2b-d100-4164-be06-0cd1d56a7e36",
      "issuedBy": "System",
      "type": "Agency"
    }
  ],
  "ticketTypes": [
    {
      "ticketTypeUniqueId": "a43db4a8-56ca-4910-a004-90d97401c199",
      "title": "پاراسل"
    },
    {
      "ticketTypeUniqueId": "1e4fc2b4-fd0d-479b-bd4c-e2f1cd8ba84c",
      "title": "شاتل"
    },
    {
      "ticketTypeUniqueId": "1f2e9a46-ab7f-4c71-9188-fe56e3e98b5d",
      "title": "بنانا"
    },
    {
      "ticketTypeUniqueId": "916fa4ac-b8ca-4395-863a-8696fa064a79",
      "title": "فلای برد"
    },
    {
      "ticketTypeUniqueId": "ff8ba4ed-2718-4a2c-b47f-27a490b0a4af",
      "title": "غواصی"
    }
  ],
  "hasActiveSans": true
}</pre>

#### Licence

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| licenceUniqueId | string |  | Yes |
| issuedBy | string |  | Yes |
| type | string |  | Yes |

**Example**
<pre>{
  "licenceUniqueId": "d6e98a2b-d100-4164-be06-0cd1d56a7e36",
  "issuedBy": "System",
  "type": "Agency"
}</pre>

#### TicketType

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| ticketTypeUniqueId | string |  | Yes |
| title | string |  | Yes |

**Example**
<pre>{
  "ticketTypeUniqueId": "a43db4a8-56ca-4910-a004-90d97401c199",
  "title": "پاراسل"
}</pre>

#### CheckItemAvailabilityAsync

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| isAvailable | boolean |  | Yes |
| title | string |  | Yes |
| ticketPrice | integer |  | Yes |
| remaining | integer |  | Yes |
| ticketTypeUniqueId | string |  | Yes |

**Example**
<pre>{
  "isAvailable": true,
  "title": "ECO | اکونومی",
  "ticketPrice": 850000,
  "remaining": 270,
  "ticketTypeUniqueId": "8d370e89-c5d9-4ae4-b068-f62760c8066e"
}</pre>

#### TempBookingAsyncRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| fullName | string |  | Yes |
| mobilePhone | string |  | Yes |
| email | string |  | Yes |
| residence | string |  | Yes |
| description | string |  | Yes |
| internalInvoiceNumber | string |  | Yes |
| bookItems | [ object ] |  | Yes |

**Example**
<pre>{
  "fullName": "پوریا شریعت زاده",
  "mobilePhone": "09120000000",
  "email": "<string>",
  "residence": "<string>",
  "description": "<string>",
  "internalInvoiceNumber": "<string>",
  "bookItems": [
    {
      "licenseUniqueId": "d6e98a2b-d100-4164-be06-0cd1d56a7e36",
      "sansUniqueId": "fe94cbd6-dd67-4d57-87e2-c887e3bed9f6",
      "ticketTypeUniqueId": "ff8ba4ed-2718-4a2c-b47f-27a490b0a4af",
      "number": 1,
      "manifest": [
        {
          "fullName": "پوریا شریعت زاده",
          "uniqueNumber": "0921557663",
          "uniqueNumberType": 1
        }
      ]
    },
    {
      "licenseUniqueId": "d6e98a2b-d100-4164-be06-0cd1d56a7e36",
      "sansUniqueId": "ea6f9f49-6ee0-4955-9fad-798aa6c555d0",
      "ticketTypeUniqueId": "916fa4ac-b8ca-4395-863a-8696fa064a79",
      "number": 3,
      "manifest": {}
    }
  ]
}</pre>

#### BookItem

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| licenseUniqueId | string |  | Yes |
| sansUniqueId | string |  | Yes |
| ticketTypeUniqueId | string |  | Yes |
| number | integer |  | Yes |
| manifest | [ object ] |  | Yes |

**Example**
<pre>{
  "licenseUniqueId": "d6e98a2b-d100-4164-be06-0cd1d56a7e36",
  "sansUniqueId": "fe94cbd6-dd67-4d57-87e2-c887e3bed9f6",
  "ticketTypeUniqueId": "ff8ba4ed-2718-4a2c-b47f-27a490b0a4af",
  "number": 1,
  "manifest": [
    {
      "fullName": "پوریا شریعت زاده",
      "uniqueNumber": "0921557663",
      "uniqueNumberType": 1
    }
  ]
}</pre>

#### Manifest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| fullName | string |  | Yes |
| uniqueNumber | string |  | Yes |
| uniqueNumberType | integer |  | Yes |

**Example**
<pre>{
  "fullName": "پوریا شریعت زاده",
  "uniqueNumber": "0921557663",
  "uniqueNumberType": 1
}</pre>

#### TempBookingAsync

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| tempBookingReference | string |  | Yes |
| expireDateTime | string |  | Yes |

**Example**
<pre>{
  "tempBookingReference": "QBLD637X6W3N48R",
  "expireDateTime": "1399/02/22 - 22:02"
}</pre>

#### FinalizingBookingAsync

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| bookingReference | string |  | Yes |
| ticketsLink | string |  | Yes |

**Example**
<pre>{
  "bookingReference": "NDPX6BD3YG",
  "ticketsLink": "https://app.2ristpanel.com/Tickets/A/NDPX6BD3YG"
}</pre>

#### FinalizingBookingAsync1

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| bookingReference | string |  | Yes |
| ticketsLink | string |  | Yes |
| eventsTickets | [ object ] |  | Yes |

**Example**
<pre>{
  "bookingReference": "15EGJL5OE9",
  "ticketsLink": "https://1va.ir/T/15EGJL5OE9",
  "eventsTickets": [
    {
      "title": "گشت تاریخی و بوم گردی",
      "link": "https://1va.ir/T/15EGJL5OE9-N38Q685P"
    },
    {
      "title": "تفریحات 2",
      "link": "https://1va.ir/T/15EGJL5OE9-F38Q985G"
    }
  ]
}</pre>

#### EventsTicket

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| title | string |  | Yes |
| link | string |  | Yes |

**Example**
<pre>{
  "title": "گشت تاریخی و بوم گردی",
  "link": "https://1va.ir/T/15EGJL5OE9-N38Q685P"
}</pre>

#### CreateTempShoppingCartForSalonSeatReservationRequest

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| SansUniqueId | string |  | Yes |
| LicenseUniqueId | string |  | Yes |
| fullName | string |  | Yes |
| mobilePhone | string |  | Yes |
| email | string |  | Yes |
| residence | string |  | Yes |
| description | string |  | Yes |
| internalInvoiceNumber | string |  | Yes |

**Example**
<pre>{
  "SansUniqueId": "<GUID>",
  "LicenseUniqueId": "<GUID>",
  "fullName": "پوریا شریعت زاده",
  "mobilePhone": "09120000000",
  "email": "<string>",
  "residence": "<string>",
  "description": "<string>",
  "internalInvoiceNumber": "<string>"
}</pre>

#### CreateTempShoppingCartForSalonSeatReservation

| Name | Type | Description | Required |
| ---- | ---- | ----------- | -------- |
| expireDateTime | string |  | Yes |
| salonUrl | string |  | Yes |
| tempBookingReference | string |  | Yes |

**Example**
<pre>{
  "expireDateTime": "1399/09/01 - 14:13",
  "salonUrl": "https://salon.2ristpanel.com/salon/7190bbe6-2ee4-4902-bdf8-f2973063a8af/1066ece0-d436-4605-b36a-5d72f9d917f9/a5eaedeb-dc18-4cd6-8e7a-e2664f5c821a",
  "tempBookingReference": "GQ15EGXYMYP9Z4K"
}</pre>
