# Отправка событий о переходе по deeplink

Для ручной отправки события о deeplink необходимо при активации Activity при ее создании выполнить следующий код:

`Kraken.trackDeepLink(url)`&#x20;

**Метод принимает на вход параметр в виде строки (string) Link - URL (обязательный) – релевантный url для web страницы, например,** [**https://rambler.ru**](https://rambler.ru/)

Пример использования в Activity на Java:

<pre><code>public class DeepLinkActivity extends AppCompatActivity {
    private EditText editText;

<strong>    @Override
</strong>    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_deeplink);

        Button button = findViewById(R.id.buttonSendLink);
        editText = findViewById(R.id.editText);

        button.setOnClickListener(
                view -> {
                    sendDeepLink();
                }
        );
    }

    private void sendDeepLink() {

        String url = editText.getText().toString();
        if (url.equals("")) {
            url = "rambler.ru";
        }
       //mTextView.setText(format(getString(R.string.send_event), url));
       Kraken.trackDeepLink(url);


<strong>   }
</strong>}
</code></pre>
