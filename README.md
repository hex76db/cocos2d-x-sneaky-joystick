# cocos2d-x-sneaky-joystick
An updated version of sneaky joystick for cocos2d-x >= 3.7

SneakyJoystick
==============

SneakyJoystick is a library that provides a 'joystick-like' features to a layer in Cocos2d-x. The library support:

- Joystick Thumb
- Joystick D-Pad
- Regular Buttons
- Holdable Buttons
- Toggleable Buttons

The project was originally created CJ Hanson (https://github.com/cjhanson). This is a port for Cocos2d-x >= 3.7


How to Use the Library
======================

The best way to use the library is to create a JoystickLayer, and then add that layer to your Game Scene.

This is an example on how to create a Joystick Thumb

auto screenSize = Director::getInstance()->getVisibleSize();

Rect joystickBaseDimensions;
joystickBaseDimensions = Rect(0, 0, 80.f, 80.0f);

Point joystickBasePosition;
joystickBasePosition = Vec2(screenSize.width * 0.2f, screenSize.height*0.2f);

SneakyJoystickSkinnedBase *joystickBase = new SneakyJoystickSkinnedBase();
joystickBase->init();
joystickBase->setPosition(joystickBasePosition);
joystickBase->setBackgroundSprite(Sprite::create("background_image.png"));
joystickBase->setThumbSprite(Sprite::create("joystick_thumb.png"));

SneakyJoystick *aJoystick = new SneakyJoystick();
aJoystick->initWithRect(joystickBaseDimensions);
aJoystick->autorelease();
joystickBase->setJoystick(aJoystick);
joystickBase->setPosition(joystickBasePosition);

auto leftJoystick = joystickBase->getJoystick();
leftJoystick->retain();
this->addChild(joystickBase);

To use it you just need to call 'getStickPosition'

This is an example on how to create a Joystick Button

Rect attackButtonDimensions = Rect(0, 0, 64.0f, 64.0f);
Point attackButtonPosition;
attackButtonPosition = Point(screenSize.width * 0.9f, screenSize.height * 0.2f);

SneakyButtonSkinnedBase *attackButtonBase = SneakyButtonSkinnedBase::create();
attackButtonBase->setPosition(attackButtonPosition);

attackButtonBase->setDefaultSprite(Sprite::create("attackBtn.png"));
attackButtonBase->setActivatedSprite(Sprite::create("attackBtn.png"));
attackButtonBase->setDisabledSprite(Sprite::create("attackBtnBlur.png"));
attackButtonBase->setPressSprite(Sprite::create("attackBtnBlur.png"));

SneakyButton *aAttackButton = SneakyButton::create();
aAttackButton->initWithRect(attackButtonDimensions);

// aAttackButton->setIsHoldable(true);
// aAttackButton->setIsToggleable(true);

attackButtonBase->setButton(aAttackButton);
attackButtonBase->setPosition(attackButtonPosition);

auto attackButton = attackButtonBase->getButton();
attackButton->retain();
addChild(attackButtonBase);

To use it you just need to call 'getValue'
