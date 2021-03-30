<template>
  <div class="footer">
    <div class="foot">
      <div class="foot-box">
        <svg
          width="64"
          height="64"
          viewBox="0 0 64 64"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <path
            d="M64 32C64 49.6733 49.6733 64 32 64C14.3267 64 0 49.6733 0 32C0 14.3267 14.3267 0 32 0C49.6733 0 64 14.3267 64 32Z"
            fill="url(#paint0_linear)"
          />
          <path
            d="M55.5698 27.8477L35.9321 8.08058C35.9072 8.05519 35.8813 8.03077 35.8545 8.00685C33.7139 6.08497 30.479 6.07765 28.3306 7.99122C28.3037 8.01466 28.2778 8.03908 28.2529 8.06447L8.43604 27.8418C7.70313 28.5733 7.70166 29.7608 8.43359 30.4937C9.16504 31.2266 10.3521 31.2276 11.085 30.4961L12.5972 28.9868V45.2832C12.5972 49.4346 15.9751 52.812 20.1265 52.812H26.9111C27.9468 52.812 28.7861 51.9727 28.7861 50.937V35.5674H35.4023V50.937C35.4023 51.9727 36.2417 52.812 37.2773 52.812H43.8735C48.0249 52.812 51.4028 49.4346 51.4028 45.2832C51.4028 44.2476 50.563 43.4082 49.5278 43.4082C48.4922 43.4082 47.6528 44.2476 47.6528 45.2832C47.6528 47.3667 45.957 49.062 43.8735 49.062H39.1523V33.6924C39.1523 32.6568 38.313 31.8174 37.2773 31.8174H26.9111C25.876 31.8174 25.0361 32.6568 25.0361 33.6924V49.062H20.1265C18.0425 49.062 16.3472 47.3667 16.3472 45.2832V25.3052C16.3472 25.2857 16.3452 25.2666 16.3447 25.2471L30.8574 10.7627C31.5669 10.1597 32.6084 10.1621 33.3159 10.7681L47.6528 25.1992V35.8599C47.6528 36.8955 48.4922 37.7349 49.5278 37.7349C50.563 37.7349 51.4028 36.8955 51.4028 35.8599V28.9741L52.9092 30.4907C53.2759 30.8594 53.7573 31.044 54.2393 31.044C54.7173 31.044 55.1953 30.8628 55.561 30.4995C56.2954 29.7695 56.2993 28.582 55.5698 27.8477Z"
            fill="white"
          />
          <defs>
            <linearGradient
              id="paint0_linear"
              x1="15.5"
              y1="5"
              x2="48.5"
              y2="64"
              gradientUnits="userSpaceOnUse"
            >
              <stop stop-color="#3BDEFF" />
              <stop offset="1" stop-color="#1C77D1" />
            </linearGradient>
          </defs>
        </svg>
        <div>
          <p style="font-weight: bold; font-size: 18px; margin-bottom: 8px">
            Новые проекты в 2021 году
          </p>
          <p style="font-size: 18px; color: #747474">
            Узнайте первым о старте реализации!
          </p>
        </div>
        <a target='_blank' class='go-to-site' href="https://bi.group/ru/filter?room_type=1&estatePerspective=true">Перейти на сайт </a>
      </div>
    </div>
    <p class='secondary'>*Электронные версии буклетов представлены не на все жилые комплексы</p>
  </div>
</template>

<script>
export default {
  name: 'footer-component',
}
</script>

<style lang="scss" scoped>
.footer {
  margin-top: 80px;
  padding-bottom: 1px;
  .foot {
    background: #f6f6f6;
    .foot-box {
      max-width: 1200px;
      margin: auto;
      padding: 30px 16px;
      display: grid;
      grid-template-columns: auto 1fr auto;
      align-items: center;
      gap: 32px;
      @media screen and (max-width: 768px){
        grid-template-columns: 1fr;
        justify-items: center;
        text-align: center;
      }
    }
  }
  .secondary{
    max-width: 1200px;
    margin: 32px auto;
    color: #01152C;
    text-align: center;
    opacity: 0.5;

  }
}

.go-to-site{
  background: #004B94;
  border-radius: 4px;
  font-weight: 500;
  font-size: 16px;
  color: white;
  padding: 10px 25px;
  &:hover{
    background: #003c78;
  }
}
</style>
