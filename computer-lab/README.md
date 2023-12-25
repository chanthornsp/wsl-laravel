# Table for Computer Lab (Database design)

## Table Users

    - id: int
    - name: string
    - email: string
    - password: string

## Table Computer Laboritorys

    - id: int
    - name: string
    - description: string
    - capacity: int
    - status: string
    - user_id: int

## Table Status

    - id: int
    - name: string
    - description: string

## Table Computers

    - id: int
    - name: string
    - description: string
    - status_id: int
    - computer_lab_id: int

## Table Types

    - id: int
    - name: string
    - description: string

## Table Components

    - id: int
    - name: string
    - model: string
    - manufacturer: string
    - description: string
    - status_id : int
    - computer_id: int
    - type_id: int
    - user_id : int
    <!-- - stock: int ??? -->

## Table Specifications

    - id: int
    - name: string
    - description: string
    - component_id: int
    - capacity: int
    - unit: string
