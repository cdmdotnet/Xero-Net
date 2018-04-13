Xero-Net-Notes
========
Added support for https://developer.xero.com/documentation/api/history-and-notes via an extension method. It has a low risk of breaking existing APIs (as it doesn't change them) and yet provides a wide range of support for existing and new API and objects. It obviously may break if the object in question doesn't support history. I've added two basic tests against the contact object and added some very light XML comments.
Version 2.2.1.13 of the Xero.API.SDK now supports this functionality (call it co-incidence that the day I send a pull request to add this functionality into the main branch and post nuget packages they also decide it's time to push their implementation), so this package is now designed for those requiring the functionality on earlier versions of the main SDK.

Example of usage:

        using Xero.Api.Common;
        
        var contact = Api.Contacts.Find(new Guid("..."));
        var allHistory = Api.Contacts.GetHistory(contact);
        var newHistory = Api.Contacts.AddNote(contact, "History was reviewd.");
