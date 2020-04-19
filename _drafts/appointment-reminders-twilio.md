---
layout: post
title: Sending appointment reminders with Twilio
date: 2020-04-19 08:00:00 +0300
image: /assets/img/twilio-notifications.jpg
tags: organisely twilio ruby-on-rails
---

Most business dealing with scheduling appointments are having troubles with no-shows. [A study published in 2017][text-reminders] revealed that sending text reminders before an appointment can increase the attendance rates.

> Blah

I'm going to present the steps required for building an automated appointment reminder system using Ruby on Rails.

Let's assume that you have a model named Event where you store each appointment and reference the user (your employee) and the client.

{% highlight ruby %}

class CreateEvents < ActiveRecord::Migration[6.0]
  def change
    create_table :events do |t|
      t.datetime :start_at, null: false
      t.datetime :end_at, null: false

      t.integer :status # enum: [:pending, :notified]

      t.references :user, index: true
      t.references :client, index: true

      t.timestamps
    end
  end
end

{% endhighlight %}

We will need a background job to cycle through tomorrow's events 

---

Need 

[text-reminders]: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5983071/
