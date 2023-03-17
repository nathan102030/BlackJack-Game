#/usr/bin/python
# -*- coding: utf-8 -*-

import random

suits = ['♠', '♣', '♦', '♥'
         ]  # Feel free to use these symbols to represent the different suits.


class Card(object):

  def __init__(self, suit, rank):
    self.suit = suit
    self.rank = rank

  def __str__(self):
    return f'{self.suit}{self.rank}'


class CardCollection(object):

  def __init__(self):
    self.cards = []

  def add_card(self, card):
    self.cards.append(card)

  def draw_card(self):
    drawn_card = self.cards.pop()
    return drawn_card

  def make_deck(self):
    for suit in suits:
      self.cards.append(Card(suit, 'A'))
      for i in range(2, 11):
        self.cards.append(Card(suit, i))
      self.cards.append(Card(suit, 'J'))
      self.cards.append(Card(suit, 'Q'))
      self.cards.append(Card(suit, 'K'))
    random.shuffle(self.cards)

  def value(self):
    if self.cards == []:
      return 0

    total = 0
    for i in range(len(self.cards)):
      rank = self.cards[i].rank
      if rank in range(2, 11):
        total += rank
      elif rank in ['J', 'Q', 'K']:
        total += 10
      elif rank == 'A':
        if total + 11 > 21: total += 1
        else: total += 11
    return total


def main():
  deck = CardCollection()
  deck.make_deck()  # initialize a fresh deck

  player_hand = CardCollection()

  player_stay = False

  while not player_stay and player_hand.value() < 22:
    drawn_card = deck.draw_card()
    player_hand.add_card(drawn_card)
    print('Player drew ' + str(drawn_card) + '.')
    print(f'Player\'s sum is {player_hand.value()}')

    if player_hand.value() > 21:
      print('Player loses.')
      break

    user_choice = input('Do you want another card? (y/n): ')

    if user_choice == 'n':
      player_stay = True
      print('It is the computer\'s turn.')

  dealer_hand = CardCollection()

  while player_stay:
    while dealer_hand.value() < 18:
      drawn_card = deck.draw_card()
      dealer_hand.add_card(drawn_card)
      print('Dealer drew ' + str(drawn_card) + '.')
      print(f'Dealer\'s sum is {dealer_hand.value()}')

    if dealer_hand.value() == 21:
      print('Dealer wins.')
      break
    elif dealer_hand.value() > 21:
      print('Player wins.')
      break
    elif dealer_hand.value() == player_hand.value():
      print('Nobody wins.')
      break
    else:
      if dealer_hand.value() > player_hand.value():
        print('Dealer wins.')
      else:
        print('Player wins.')
      break


if __name__ == "__main__":
  main()
