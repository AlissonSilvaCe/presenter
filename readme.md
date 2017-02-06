# codecasts/presenter

CODECASTS's View Presenter

Easy View Presenters

Install

Pull this package in through Composer.

{
    "require": {
        "codecasts/presenter": "1.0.1*"
    }
}

Usage

namespace App\Presenter;
use Codecasts\Presenter\Presenter;

class UserPresenter extends Presenter {

    public function fullName()
    {
        return $this->first . ' ' . $this->last;
    }

    public function accountAge()
    {
        return $this->created_at->diffForHumans();
    }

}

Example: Laravel User model.

<?php
use Illuminate\Database\Eloquent\Model;
use Laracasts\Presenter\Presentable;
use App\Presenter\UsePresenter;

class User extends Model {

    use Presentable;

    protected $presenter = UserPresenter::class;

}

That's it! You're done. Now, within your view, you can do:

    <h1>Hello, {{ $user->present()->fullName }}</h1>
