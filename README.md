# THailand Baht Token

**THailand Baht Token**


![THBT](https://token.gsotm.com/thbt/icon.png "THBT")


THBT is a virtual currency that links cryptocurrency to the legal currency of Thai baht. It is a token based on the stable value of Thai baht (THB) launched by the Global Sojourn Group. 1THBT=1 baht, and users can 1:1 exchanged THBT and THB at any time. Global Sojourn Group strictly abides by the 1:1 reserve guarantee, that is, for every THBT token issued, its bank account will have 1 baht fund guarantee.  THBT is linked to the legal Thai baht currency, and each THBT will be symbolically associated with the government-supported legal currency, effectively preventing the price fluctuation of THBT. Basically, the value of one THBT is equal to 1 baht.

#### CODE
```javascript
contract Token is ERC20 {
    string private _name;
    string private _symbol;
    uint8 private _decimals;

    /**
     * @dev Sets the values for `name`, `symbol`, and `decimals`. All three of
     * these values are immutable: they can only be set once during
     * construction.
     */
    constructor (uint256 _initialSupply,string memory name, string memory symbol, uint8 decimals) public {
        _name = name;
        _symbol = symbol;
        _decimals = decimals;
        _mint(msg.sender, _initialSupply * (10 ** uint256(decimals)));
    }

    /**
     * @dev Returns the name of the token.
     */
    function name() public view returns (string memory) {
        return _name;
    }

    /**
     * @dev Returns the symbol of the token, usually a shorter version of the
     * name.
     */
    function symbol() public view returns (string memory) {
        return _symbol;
    }

    /**
     * @dev Returns the number of decimals used to get its user representation.
     * For example, if `decimals` equals `2`, a balance of `505` tokens should
     * be displayed to a user as `5,05` (`505 / 10 ** 2`).
     *
     * Tokens usually opt for a value of 18, imitating the relationship between
     * Ether and Wei.
     *
     * NOTE: This information is only used for _display_ purposes: it in
     * no way affects any of the arithmetic of the contract, including
     * {IERC20-balanceOf} and {IERC20-transfer}.
     */
    function decimals() public view returns (uint8) {
        return _decimals;
    }

    function issue(uint256 _amount) public onlyOwner returns (bool){
        _mint(msg.sender, _amount * (10 ** uint256(decimals())));
        emit Issue(_amount);
        return true;
    }


    // Called when new token are issued
    event Issue(uint amount);
}

```

