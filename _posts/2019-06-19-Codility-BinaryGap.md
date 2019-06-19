---
layout: post
title:  "BinaryGap"
tags:
  - Codility
hero: /../assets/resources/img/codility/binaryGap/b1.png
overlay: blue
published: true

---
해봐야지 해봐야지 하면서 미루다가 <a href="https://app.codility.com/programmers/">Codility</a>가입하고 Lessons에 들어갔다.
{: .lead}
전부 영어라 뭐가 뭔지 몰랐지만 일단 Lesson 1을 시작했다. Start 버튼을 누르니
<!–-break-–>
<img src='/../assets/resources/img/codility/binaryGap/b1.png' alt='b1'>
화면이 딱! 뭔가 정말 시험을 보는 느낌이라서 선뜻 시작버튼을 누르기 망설여졌다. 
> A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the binary representation of N.

For example, number 9 has binary representation 1001 and contains a binary gap of length 2. The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. The number 20 has binary representation 10100 and contains one binary gap of length 1. The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary gaps.

Write a function:

class Solution { public int solution(int N); }

that, given a positive integer N, returns the length of its longest binary gap. The function should return 0 if N doesn't contain a binary gap.

For example, given N = 1041 the function should return 5, because N has binary representation 10000010001 and so its longest binary gap is of length 5. Given N = 32 the function should return 0, because N has binary representation '100000' and thus no binary gaps.

Write an efficient algorithm for the following assumptions:

N is an integer within the range [1..2,147,483,647].
Copyright 2009–2019 by Codility Limited. All Rights Reserved. Unauthorized copying, publication or disclosure prohibited.

