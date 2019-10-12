# hello-world
<context>
  <input pattern="* (привет*|здравствуй*) *">
    <!-- Здороваемся если знаем имя -->
    <output value="Привет $UserName!" if="full($UserName)"/>

    <!-- Или переходим к внутреннему контексту чтобы выяснить имя -->
    <context if="empty($UserName)">
      <output value="Привет! А как тебя зовут?"/>

        <input pattern="$Text">
          <!-- Сохранем мия пользователя в переменную UserName -->
          <var name="UserName" value="cap($Text)" scope="user"/>
          <output value="Приятно познакомиться, $UserName!"/>
        </input>
      </context>
    </input>
</context>
