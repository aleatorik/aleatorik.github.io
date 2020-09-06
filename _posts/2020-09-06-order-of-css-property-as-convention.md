---
layout: post
title: CSS 속성 순서에 대한 컨벤션
category: TIL (Today I Learned)
tags: [TIL (Today I Learned)]
---

```
- Layout Properties (position, float, clear, display)
- Box Model Properties (width, height, margin, padding)
- Visual Properties (color, background, border, box-shadow)
- Typography Properties (font-size, font-family, text-align, text-transform)
- Misc Properties (cursor, overflow, z-index)
```

## 위의 컨벤션 적용 전

```
const Button = styled.button`
  border-bottom: 2px solid #e0e0e0;
  color: #616161;
  font-size: 14px;
  padding: 14px;
  width: 50%;
`;
```

## 컨벤션 적용 후

```
const Button = styled.button`
  width: 50%;
  padding: 14px;
  color: #616161;
  border-bottom: 2px solid #e0e0e0;
  font-size: 14px;
`;
```
