---
layout: plain
title: "Start a Project"
permalink: /start.html
description:
  Hire an orchestrated team of remotely working freelancers,
  and enjoy the quality of code and efficiency of management.
keywords:
  - hire software developer
  - remote programmer hire
  - hire programmer
  - start working remotely
  - hire a programmer
---

Please fill out this form and we get back to you in a few hours:

<form name="hire" name="form" ng-submit="submit()">
  <p>
    <label>Your email</label><br/>
    <input name="email" type="email" tabindex="1"
      style="width:11em" maxlength="100" ng-model="email" required/>
  </p>
  <p>
    <label>Budget, in USD<br/>
    <input name="budget" type="text" tabindex="2"
      style="width:8em" maxlength="15" ng-model="budget" required/><br/>
    <span class="help">We are not big fans of
    strict estimates, mostly because they just don't work, as
    <a href="">this article</a>
    explains. However, your expectations of </span>
  </p>
  <p>
    <label><a href="http://www.netbout.com">Netbout</a> account name</label><br/>
    <input name="netbout" style="width:8em" tabindex="9"
      placeholder="[a-zA-Z0-9]+" pattern="[a-zA-Z0-9]+"
      maxlength="50" ng-model="netbout" required/><br/>
    <span class="help">We use Netbout for non-project discussions
    related to payments, disciplinary actions, ratings, performance
    appraisals, etc. Netbout integrates our management and automated
    reporting tools. If you don't have a Netbout account, create one now;
    it should take less than a minute. Don't forget to register your email
    there to stay tuned for updates.</span>
  </p>
  <p>
    <label>How do we pay you?</label><br/>
    <input name="wallet" style="width:13em" tabindex="10"
      maxlength="100" ng-model="wallet" required/><br/>
    <span class="help">There are two options at the moment:
    <a href="http://www.paypal.com">PayPal</a> or <a href="http://www.upwork.com">Upwork</a>.
    If you want us to pay through PayPal, just give us the email of
    your PayPal account. If you want to use Upwork, provide us a link to your Upwork profile.</span>
  </p>
  <p>
    <label>Tell us briefly about yourself</label><br/>
    <textarea name="info" style="width:21em;height:4em" tabindex="11"
      ng-model="info" required></textarea><br/>
    <span class="help">Read <a href="http://www.yegor256.com/2014/10/29/how-much-do-you-cost.html">this article</a>
    and explain briefly why you think you're better than
    others and why we should work with you.
    It would be great if you could solve
    <a href="https://github.com/teamed/quiz">this quiz</a>,
    submit a pull request with your corrections, and post the link
    to it right here.</span>
  </p>
  <p>
    <label>How did you find us?</label><br/>
    <input name="ref" style="width:9em" tabindex="12"
      maxlength="200" ng-model="ref" required/><br/>
    <span class="help">If you have a reference code, post it
      here and the person who gave it to you will receive a bonus
      &mdash; if we hire you :)</span>
  </p>
  <p>
    <button id='submit' tabindex="13">Submit</button><br/>
    <span class="help">Right after you click this button, we'll create a new
    conversation in Netbout. One of us will reply to you
    within 24 hours. Keep in mind that we reject over 80 percent of
    applications.</span>
  </p>
</form>

<script>
angular.module('teamed', []).controller(
  'Main',
  [
    '$scope',
    function($scope) {
      $scope.submit = function() {
        var text =
          'I would like to join you\n\n'
          + 'name=' + $scope.name
          + '; bout=here'
          + '; rate=$' + $scope.rate + '/hr'
          + '; roles=DEV,IMP'
          + '; skills=' + $scope.skills
          + '; phone=' + $scope.phone
          + '; country=' + $scope.country
          + '; address=' + $scope.address
          + '; email=' + $scope.email
          + '; github=' + $scope.github
          + '; netbout=' + $scope.netbout
          + '; wallet=' + $scope.wallet
          + '; ref=' + $scope.ref
          + '\n\n' + $scope.info;
        var url = 'http://www.netbout.com/start?post='
          + encodeURIComponent(text)
          + '&invite=alice&rename='
          + encodeURIComponent($scope.github);
        if ($scope.ref.toLowerCase() === 'yegor') {
          url += '&invite=yegor256&post=@yegor256+please+take+a+look';
        } else {
          url += '&post=@alice+interview+' + $scope.netbout;
        }
        window.location = url;
      }
    }
  ]
);
</script>