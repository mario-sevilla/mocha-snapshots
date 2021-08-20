# Mocha Snapshots
Snapshot/regression testing for using with Mocha, specially for React+Enzyme users.

## Install it
`npm i @junglescoutofficial/mocha-snapshots --save-dev`

## Use it
```es6
import { expect } from 'chai';
import { shallow } from 'enzyme';
import MyComponent from './path/to/MyComponent';

describe('<MyComponent />', () => {
  it('should match snapshot', () => {
    const wrapper = shallow(<MyComponent />)
    
    // You can match Enzyme wrappers
    expect(wrapper).to.matchSnapshot();
    
    // Strings
    expect('you can match strings').to.matchSnapshot();
    
    // Numbers
    expect(123).to.matchSnapshot();
    
    // Or any object
    expect({ a: 1, b: { c: 1 } }).to.matchSnapshot();
   
  });
});
```

## Run your tests
Add a require argument to your test script/command 

`mocha --require @junglescoutofficial/mocha-snapshots`

## Disable classNames cleanup
To prevent false mismatches, mocha-snapshots sanitizes className props by default. You can disable this behavior before running your tests:
```js
import mochaSnapshots from '@junglescoutofficial/mocha-snapshots';

mochaSnapshots.setup({ sanitizeClassNames: false })
```

## Update snapshots
Set an environment variable `UPDATE` and run your test script or add the flag `--update`  when running Mocha:

```
UPDATE=1 mocha --require @junglescoutofficial/mocha-snapshots
``` 
or
```
mocha --require @junglescoutofficial/mocha-snapshots --update
```
