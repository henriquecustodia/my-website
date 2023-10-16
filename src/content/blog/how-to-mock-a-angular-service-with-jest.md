---
title: "How to mock an Angular service with Jest"
description: It is a simple but still an useful way to mock an Angular service with Jest
pubDatetime: 2023-10-15T11:21:30.000Z
tags:
  - angular
  - jest
  - testing
draft: false
feature: false
ogImage: "@assets/images/james-lee-qSf_4bNsoWc-unsplash.jpg"
---

![james-lee-qSf_4bNsoWc-unsplash.jpg](@assets/images/james-lee-qSf_4bNsoWc-unsplash.jpg)

Recently I needed to mock a service in an Angular app that uses Jest as its test runner but I didn't remember very well how to do that.

Doing some researchs on web I saw lots of confusing solutions, but after some time I found what I needed.

Here is the solution that solved my problem:

```ts
describe('SearchService', () => {
  let service: SearchService; // the service that will test

  let booksServiceMock!: { getBooks: jest.Mock }; // the mock value

  beforeEach(() => {
    // create an object that mock the getBooks method from BooksService
    booksServiceMock = {
      getBooks: jest.fn(),
    };

    TestBed.configureTestingModule({
      providers: [
        {
          provide: BooksService,
          useValue: booksServiceMock, // uses the mock
        },
      ],
    });

    service = TestBed.inject(SearchService);
  });

  describe('when there is NO data', () => {
    it('should return an empty array', () => {

      // set the return value of the mocking function
      booksServiceMock.getBooks.mockReturnValue([]);

      expect(service.search('test')).toEqual([]);

      expect(service.search('')).toEqual([]);
    });
  });
```

Hope that code could be useful for you as it was useful for me!

(Actually I'm writing this post to the future me haha)
