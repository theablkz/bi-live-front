<template>
  <div class="footer">
    <div class='footer-head'>
      <div class='contactss'>
        <div>
          <h2>Затрудняетесь с выбором? Мы рядом!</h2>
          <p>Оставьте заявку и Менеджер свяжется с <br> вами и поможет определиться с выбором</p>
        </div>
        <div>
          <div class="contacts">
            <a href="tel:360">
              <div class="call-phone">
                <div class="phone">
                  <img src="~assets/image/icons/phone-call.svg" alt />
                  <h3>360</h3>
                </div>
                <p>Бесплатно с мобильного</p>
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
    <div class="footer__licence">
      <p class="">
        Настоящая реклама, в соответствии со ст. 395 ГК РК, не является публичной офертой.
      </p>
    </div>
    <div class="footer-content">
      <div class="footer-content__contacts">
        <img class="logo" src="~assets/image/icons/logo.svg" alt="bi group" />

        <div class="contacts">
          <a href="tel:360">
            <div class="call-phone">
              <div class="phone">
                <img src="~assets/image/icons/phone-call.svg" alt />
                <h3>360</h3>
              </div>
              <p>Бесплатно с мобильного</p>
            </div>
          </a>
        </div>
      </div>
      <div class="footer-content__media">
        <a target="_blank" href="https://www.youtube.com/user/BIGroupHolding">
          <img src="~assets/image/social/youtube.svg" alt />
        </a>
        <a target="_blank" href="https://www.facebook.com/bigroup.holding/">
          <img src="~assets/image/social/facebook.svg" alt />
        </a>
        <a target="_blank" href="https://twitter.com/bigroup_kz">
          <img src="~assets/image/social/twitter.svg" alt />
        </a>
        <a target="_blank" href="https://www.instagram.com/bi.group/">
          <img src="~assets/image/social/instagram.svg" alt />
        </a>
        <a target="_blank" href="https://vk.com/bigroupholding">
          <img src="~assets/image/social/vk.svg" alt />
        </a>
      </div>
    </div>
  </div>
</template>

<style lang="scss">
.footer {
  margin-top: 80px;
  background: #f1f1f1;
  border-top: 1px solid #E0E0E0;

  .footer-head{
    padding: 2.4rem 0;
    background: #F6F6F6;
    .contactss{
      padding: 0 1.6rem;
      display: flex;
      justify-content: space-between;
      max-width: 120rem;
      margin: auto;
      h2{
        font-weight: bold;
        font-size: 30px;
        line-height: 40px;
        color: #272727;
      }
      p{
        font-weight: normal;
        font-size: 16px;
        line-height: 18px;
        color: #272727;
      }
      .contacts{
        .call-phone {
          .phone {
            justify-content: flex-end;
          }
        }
      }
      @media screen and (max-width: 768px){
        flex-direction: column;
        align-items: center;
        text-align: center;
        p {
          margin-bottom: 24px;
        }
        .contacts{
          .call-phone {
            .phone {
              justify-content: center;
            }
          }
        }
      }
    }
  }

  &__licence {
    padding: 0 1.6rem;
    max-width: 120rem;
    margin: auto;
    p{
      padding: .8rem 0;
    }
  }
  .footer-content {
    padding: 0 1.6rem 2.4rem;
    max-width: 120rem;
    margin: 3rem auto auto auto;
    display: flex;
    justify-content: space-between;
    &__contacts {
      display: grid;
      grid-template-columns: auto auto;
      gap: 4rem;

    }
    &__media {
      display: grid;
      grid-template-columns: repeat(5, 3.2rem);
      grid-template-rows: 3.2rem;
      gap: 1.6rem;
    }
    @media screen and (max-width: 768px) {
      flex-direction: column;
      &__contacts {
        gap: 1.6rem;
        margin-bottom: 4rem;
      }
    }
  }
  .contacts {
    .call-phone {
      .phone {
        color: #004b94;
        display: flex;
        justify-content: flex-start;
        h3 {
          color: inherit;
          font-size: 1.8rem;
          margin-left: 0.5rem;
        }
      }
      p {
        color: #333333;
        font-weight: 500;
      }
    }
  }
}
</style>
