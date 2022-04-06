<script>
  import currency from 'currency.js';

  let output = '100K';
  let price = 16.00;
  let fillLower = '50%';
  const discount = 25;

  const handleInput = (e) => {
    let values = [
      ['10K', 8.00],
      ['50K', 12.00],
      ['100K', 16.00],
      ['500K', 24.00],
      ['1M', 36.00],
    ];
    output = values[e.target.value][0];
    price = values[e.target.value][1];
    fillLower = (e.target.value / e.target.max) * 100 + '%';
  }

  const handleToggle = (e) => {
    if (e.target.checked) {
      price = price - (price * discount / 100);
    } else {
      price = price / ((100 - discount) / 100);
    }
  }
</script>

<form class="fade-up-2">
  <div class="form-main">
    <div class="form-header">
      <p class="views">
        <output>{output}</output> Pageviews
      </p>

      <div class="form-range" style="--range: {fillLower}">
        <label for="pageviews" class="sr-only">Page views</label>
        <input id="pageviews" type="range" min="0" value="2" max="4" step="1" on:input={handleInput}>
      </div>

      <p class="price">
        <strong><output>{currency(price, { symbol: "£"}).format()}</output></strong> / month
      </p>
    </div>

    <!-- Rounded switch -->
    <div class="control">
      <label for="billing">
        <span class="label">
          Monthly Billing
        </span>

        <span class="switch">
          <span class="sr-only">Toggle billing</span>
          <input type="checkbox" id="billing" on:change={handleToggle}>
          <span class="slider round"></span>
        </span>

        <span class="label">
          <span>Yearly Billing</span>

          <span class="discount">
            <span class="discount-mobile">-25%</span>
            <span class="discount-desktop">25% discount</span>
          </span>
        </span>
      </label>
    </div>
  </div>

  <div class="form-footer">
    <ul>
      <li>Unlimited websites</li>
      <li>100% data ownership</li>
      <li>Email reports</li>
    </ul>

    <div>
      <button>Start my trial</button>
    </div>
  </div>
</form>

<style>
  form {
    font-size: 0.8125rem;
    min-height: 478px;
    display: flex;
    flex-direction: column;
    text-align: center;
    background: var(--white);
    border-radius: 0.5rem;
    box-shadow: 0 1rem 1rem hsl(227deg 35% 25% / 5%);
  }

  .form-range {
    margin-bottom: 1.3rem;
  }

  .form-main {
    padding: 2rem 1.5rem 2.375rem;
  }

  .form-footer {
    padding: 1.5rem 1.5rem 2rem;
    border-top: 1px solid var(--light-grayish-blue);
  }

  .views {
    font-weight: 800;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    margin-bottom: 1.375rem;
  }

  .price {
    font-size: 0.875rem;
    display: flex;
    align-items: center;
    justify-content: center;
    margin-bottom: 1.875rem;
  }

  .price strong {
    font-size: 2rem;
    letter-spacing: -0.025em;
    margin-right: 0.625rem;
    color: var(--dark-desaturated-blue);
  }

  .control {
    display: flex;
    align-items: center;
    justify-content: center;
    margin-left: -0.875rem;
  }

  label {
    font-size: 0.75rem;
    position: relative;
    display: flex;
    align-items: center;
    cursor: pointer;
  }

  .discount {
    font-size: 0.625rem;
    font-weight: 800;
    line-height: 1.125rem;
    display: inline-block;
    background-color: var(--light-grayish-red);
    color: var(--light-red);
    padding: 0 0.5rem;
    white-space: nowrap;
    border-radius: 1.125rem;
    position: absolute;
    left: 100%;
    margin-left: 0.25rem;
  }

  .discount-desktop {
    display: none;
  }

  ul {
    font-size: 0.75rem;
    list-style: none;
    margin: 0 0 1.875rem;
    padding-left: 0;
  }

  li {
    display: flex;
    align-items: center;
    justify-content: center;
  }

  li + li {
    margin-top: 0.5rem;
  }

  li::before {
    content: '';
    display: block;
    background: url('/icon-check.svg') no-repeat top left;
    background-size: 9px 8px;
    width: 9px;
    height: 8px;
    margin-right: 0.875rem;
  }

  button {
    font-size: 0.75rem;
    font-weight: 800;
    max-width: 170px;
    width: 100%;
    height: 2.5rem;
    color: var(--pale-blue);
    border: 0;
    border-radius: 2.5rem;
    background-color: var(--dark-desaturated-blue);
    cursor: pointer;
    transition: color 0.15s;
  }

  button:hover,
  button:focus {
    color: var(--white);
  }

  @media (min-width: 992px) {
    form {
      min-height: 0;
      box-shadow: 0 1rem 1rem hsl(227deg 35% 25% / 7%);
    }

    .form-main {
      padding: 2.25rem 3rem 2.5rem;
    }

    .form-header {
      display: flex;
      flex-wrap: wrap;
      align-items: center;
    }

    .views {
      font-size: 0.9375rem;
      order: 1;
      text-align: left;
      transform: translate(-4px, 1px);
    }

    .price {
      font-size: 16px;
      order: 2;
      margin-bottom: 1.2rem;
    }

    .price strong {
      font-size: 2.5rem;
    }
    
    .form-range {
      order: 3;
      margin-bottom: 2.5rem;
    }

    .views,
    .price {
      flex: 1 0 50%;
      max-width: 50%;
    }

    .price strong {
      margin-left: auto;
    }

    .form-range {
      width: 100%;
    }

    .control {
      margin-left: 0;
    }

    .discount {
      margin-left: 0.5rem;
      padding: 0 0.5rem;
    }

    .discount span {
      position: static;
      width: auto;
      height: auto;
      margin: 0;
      overflow: visible;
      clip: none;
    }

    .discount-mobile {
      display: none;
    }

    .discount-desktop {
      display: block;
    }

    .form-footer {
      display: flex;
      align-items: center;
      padding: 2rem 2.75rem 1.875rem 2.875rem;
    }

    ul,
    .form-footer div {
      flex: 1 0 50%;
      max-width: 50%;
    }

    .form-footer div {
      text-align: right;
    }

    ul {
      margin-bottom: 0;
    }

    li {
      justify-content: flex-start;
    }

  }
</style>
