=================================
Before scheduled date reservation
=================================

The *Before scheduled date* reservation method allows users to select a specific number of days that
will act as the maximum number of days **before** a scheduled delivery date that products included
in a sales order (SO) should be reserved.

.. seealso::
   :doc:`About reservation methods <../reservation_methods>`

Configuration
=============

To set the reservation method to *Before scheduled date*, navigate to :menuselection:`Inventory app
--> Configuration --> Operations Types`.

In the :guilabel:`General` tab, locate the :guilabel:`Reservation Method` field, and select
:guilabel:`Before scheduled date`.

.. image:: before_scheduled_date/before-scheduled-date-configuration.png
   :align: center
   :alt: Reservation method field on delivery order operation type form.

Once selected, a new :guilabel:`Reserve before scheduled date` field appears below. From this field,
the number of :guilabel:`days before` and :guilabel:`days before when starred` can be changed from
the default `0`.

Changing the :guilabel:`days before` value changes the maximum number of days before a scheduled
date that products should be reserved.

Changing the :guilabel:`days before when starred` value changes the maximum number of days before
a scheduled date that products should be reserved for starred (favorited) transfers.

.. example::
   In the image below, the :guilabel:`days before` value is set to `2` days before, and the
   :guilabel:`days before when starred` value is set to `3`.

   This means that products will be reserved two days before the scheduled delivery date for normal
   orders, and three days before the scheduled delivery date for starred (favorited) transfers.

   .. image:: before_scheduled_date/before-scheduled-date- days-before.png
      :align: center
      :alt: Reserve before scheduled date field with set numerical values.

   This is the configuration applied for the following workflow below.

Edit product form
-----------------

Before beginning the workflow, first add a *customer lead time* to the product that will be sold. To
do so, navigate to :menuselection:`Products --> Products`, and select the desired product.

Click the :guilabel:`Inventory` tab, and under the :guilabel:`Logistics` section, change the value
in the :guilabel:`Customer Lead Time` field to `5` days. This sets the scheduled delivery date for
this specific product to five days after the creation date of the sales order.

.. image:: before_scheduled_date/before-scheduled-date-customer-lead-time.png
   :align: center
   :alt: Product form with customer lead time set in Inventory tab.

Workflow
========

To see the *Before scheduled date* reservation method in action, create a new :abbr:`SO (sales
order)` by navigating to :menuselection:`Sales app --> New`.

Add a customer in the :guilabel:`Customer` field, then, in the :guilabel:`Order Lines` tab, click
:guilabel:`Add a product`, and select a product to add to the quotation from the drop-down menu.
Finally, in the :guilabel:`Quantity` column, adjust the desired quantity of the product to sell.

Once ready, click :guilabel:`Confirm` to confirm the sales order.

Click the green :guilabel:`📈 (forecast graph)` icon on the product line to reveal the product's
:guilabel:`Availability` tooltip. This tooltip reveals the reserved number of units for this order.
Because the reservation method is set to *Before scheduled date*, the :guilabel:`Reserved` quantity
reads `0 Units`.

However, below that quantity reads `Available in stock`. This is because the quantity is available,
but the scheduled date is five days from the order date. Since reservation isn't until two days
before the scheduled delivery, it will not reserve the products until then.

.. image:: before_scheduled_date/before-scheduled-date-availability-tooltip.png
   :align: center
   :alt: Confirmed sales order with product availability tooltip selected.

Click the :guilabel:`Delivery` smart button to see the delivery order form.

On the :guilabel:`Delivery Order` form, the status in the :guilabel:`Product Availability` field is
listed as `Available`, in yellow text instead of green. This is because there is sufficient stock on
hand for this order, but no quantity has been reserved yet.

Note the :guilabel:`Scheduled Date` field above the :guilabel:`Product Availability` field displays
the date five days from the order creation date. This indicates that the products will not be
reserved until three days from today's date (two days before the scheduled delivery date).

.. image:: before_scheduled_date/before-scheduled-date-delivery-order-form.png
   :align: center
   :alt: Delivery order form with product availability and reserved quantity.

In the :guilabel:`Operations` tab on the :guilabel:`Product` line, the numbers in the
:guilabel:`Demand` column and the :guilabel:`Quantity` column do not match (in this case, the
:guilabel:`Demand` column lists `10.00`, while the :guilabel:`Quantity` column lists `0`.

.. tip::
   If the product(s) in the :abbr:`SO (sales order)` should be reserved sooner than the scheduled
   reservation date, the reservation can be manually "overridden". To manually reserve the products
   sooner than scheduled, click :guilabel:`Check Availability` at the top of the form.

   This turns the `Available` status in the :guilabel:`Product Availability` field green, and
   changes the number in the :guilabel:`Quantity` column to `10.00`, so it matches the
   :guilabel:`Demand` column.

   Once ready, click :guilabel:`Validate`.

.. seealso::
   - :doc:`Manual reservation <../reservation_methods/manually>`
   - :doc:`At confirmation reservation <../reservation_methods/at_confirmation>`
