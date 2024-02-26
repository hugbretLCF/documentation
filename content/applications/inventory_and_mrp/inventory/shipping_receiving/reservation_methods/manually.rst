==================
Manual reservation
==================

Unlike the *At Confirmation* reservation method, the *Manually* reservation method does **not**
reserve products automatically.

Instead, once a sales order (SO) is confirmed, product availability **must** be checked manually,
and the required quantity **must** be reserved manually.

.. seealso::
   :doc:`About reservation methods <../reservation_methods>`

Configuration
=============

To set the reservation method to *Manually*, navigate to :menuselection:`Inventory app -->
Configuration --> Operations Types`.

In the :guilabel:`General` tab, locate the :guilabel:`Reservation Method` field, and select
:guilabel:`Manually`.

.. image:: manually/manually-operations-type.png
   :align: center
   :alt: Reservation method field on delivery order operation type form.

Workflow
========

To see the *Manually* reservation method in action, create a new :abbr:`SO (sales order)` by
navigating to :menuselection:`Sales app --> New`.

Add a customer in the :guilabel:`Customer` field, then, in the :guilabel:`Order Lines` tab, click
:guilabel:`Add a product`, and select a product to add to the quotation from the drop-down menu.
Finally, in the :guilabel:`Quantity` column, adjust the desired quantity of the product to sell.

Once ready, click :guilabel:`Confirm` to confirm the sales order.

Click the green :guilabel:`forecast graph` icon on the product line to reveal the product's
:guilabel:`Availability` tooltip. This tooltip reveals the reserved number of units for this order.
Because the reservation method is set to *Manually*, the :guilabel:`Reserved` quantity reads `0
Units`.

However, below that quantity reads `Available in stock`. This is because the quantity is available,
but must be manually reserved.

.. image:: manually/manually-availability-tooltip.png
   :align: center
   :alt: Confirmed sales order with product availability tooltip selected.

Once the :abbr:`SO (sales order)` is confirmed, navigate to the :menuselection:`Inventory app`, and
locate the :guilabel:`Delivery Orders` card on the :guilabel:`Inventory Overview` page.

The :guilabel:`Delivery Orders` card displays the current status of live orders, including those
with a *Waiting* status. Orders with this status indicate that the products in those orders have
either not been reserved yet, or are not in stock at all.

.. image:: manually/manually-delivery-orders-card.png
   :align: center
   :alt: Delivery orders task card with waiting status orders.

To see the :abbr:`SO (sales order)` created previously, click the :guilabel:`X Waiting` button on
the card (in this case, `8 Waiting`).

Locate the delivery order (DO) tied to the :abbr:`SO (sales order)` that was previously created, and
click the line to view it.

On the :guilabel:`Delivery Order` form, the status in the :guilabel:`Product Availability` field is
listed as `Available`, in yellow text instead of green. This is because there is sufficient stock on
hand for this order, but no quantity has been reserved yet.

In the :guilabel:`Operations` tab on the :guilabel:`Product` line, the numbers in the
:guilabel:`Demand` column and the :guilabel:`Quantity` column do no match (in this case, the
:guilabel:`Demand` column lists `10.00`, while the :guilabel:`Quantity` column lists `0`.

.. image:: manually/manually-delivery-order-form.png
   :align: center
   :alt: Delivery order form with product availability and reserved quantity.

To manually reserve the specified quantity of the product for this order, click the
:guilabel:`Check Availability` button at the top of the form. Doing so turns the `Available` status
in the :guilabel:`Product Availability` field green, and changes the number in the
:guilabel:`Quantity` column to `10.00`, so it matches the :guilabel:`Demand` column.

Once ready, click :guilabel:`Validate`.

.. tip::
   Multiple orders with a *Waiting* status can be manually reserved at once and set to *Ready*
   status.

   To do that, from the :guilabel:`Inventory Overview` page, click the :guilabel:`X Waiting` button
   on the :guilabel:`Delivery Orders` card.

   Then, click the :guilabel:`checkboxes` to the left of each desired order, or click the
   :guilabel:`checkbox` in the header row to select all orders on the page. Then, click the
   :guilabel:`Check Availability` button at the top of the page.

   If the product(s) included in every order have enough stock on hand, this reserves the products
   and moves the order into :guilabel:`Ready` status, and disappears the order from the
   :guilabel:`Waiting` list. If there is not enough stock on hand, the order will retain its current
   status, and remain on the list.

   .. image:: manually/manually-check-availability.png
      :align: center
      :alt: List of orders in waiting status and check availability button.

.. seealso::
   - :doc:`At confirmation reservation <../reservation_methods/at_confirmation>`
   - :doc:`Before scheduled date reservation <../reservation_methods/before_scheduled_date>`
