---
layout: post
title: Sending appointment reminders with Twilio
date: 2020-04-19 08:00:00 +0300
image: /assets/img/twilio-notifications.jpg
tags: Organisely Twilio
---

Most business dealing with scheduling appointments had troubles with no-shows. [A study published in 2017][text-reminders] revealed that sending text reminders before an appointment can increase the attendance rates.

Let's assume that you have a model named Event where you store each appointment and reference the user.

{% highlight ruby %}

class CreateEvents < ActiveRecord::Migration[6.0]
  def change
    create_table :events do |t|
      t.datetime :start_at, null: false
      t.datetime :end_at, null: false

      t.references :user, index: true
      t.references :client, index: true

      t.timestamps
    end
  end
end

{% endhighlight %}

[text-reminders]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5983071/
