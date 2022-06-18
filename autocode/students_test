package coverage

import (
	"fmt"
	"os"
	"strconv"
	"strings"
	"testing"
	"time"
)

// DO NOT EDIT THIS FUNCTION
func init() {
	content, err := os.ReadFile("students_test.go")
	if err != nil {
		panic(err)
	}
	err = os.WriteFile("autocode/students_test", content, 0644)
	if err != nil {
		panic(err)
	}
}

// WRITE YOUR CODE BELOW

func TestPeople_Len(t *testing.T) {
	fmt.Println("TestPeople_Len triggered")
	var expectedNbrOfPeople = 4
	p1 := Person{}
	p2 := Person{}
	p3 := Person{}
	p4 := Person{}

	people := People{p1, p2, p3, p4}
	if got := people.Len(); got != expectedNbrOfPeople {
		t.Errorf("expected: %d, but got: %d", expectedNbrOfPeople, got)
	}

}

// TestPeople_Less1 to compare by birthday
func TestPeople_Less1(t *testing.T) {
	fmt.Println("TestPeople_Less1 triggered")
	p1 := Person{
		firstName: "Nurlan",
		lastName:  "Ikhsan",
		birthDay:  time.Date(1996, time.Month(1), 15, 0, 0, 0, 0, time.Local),
	}
	p2 := Person{
		firstName: "Nurzhan",
		lastName:  "Ikhsan",
		birthDay:  time.Date(1997, time.Month(12), 7, 0, 0, 0, 0, time.Local),
	}
	p3 := Person{
		firstName: "Abylai",
		lastName:  "Iskander",
		birthDay:  time.Date(1996, time.Month(6), 9, 0, 0, 0, 0, time.Local),
	}

	people := People{p1, p2, p3}
	indx0 := 0
	indx1 := 1
	ok := people.Less(indx0, indx1)
	if ok {
		t.Errorf("expected to be %v < %v, but got: %v", p1.birthDay, p2.birthDay, ok)
	}

}

// TestPeople_Less2 to compare by firstname
func TestPeople_Less2(t *testing.T) {
	fmt.Println("TestPeople_Less2 triggered")
	p1 := Person{
		firstName: "Nurlan",
		lastName:  "Ikhsan",
		birthDay:  time.Date(1996, time.Month(1), 15, 0, 0, 0, 0, time.Local),
	}
	p2 := Person{
		firstName: "Nurzhan",
		lastName:  "Ikhsan",
		birthDay:  time.Date(1997, time.Month(12), 7, 0, 0, 0, 0, time.Local),
	}
	p3 := Person{
		firstName: "Abylai",
		lastName:  "Iskander",
		birthDay:  time.Date(1996, time.Month(1), 15, 0, 0, 0, 0, time.Local),
	}

	people := People{p1, p2, p3}
	indx0 := 0
	indx1 := 2
	ok := people.Less(indx0, indx1)
	if ok {
		t.Errorf("expected to be %v < than %v, but got vice verse: %v", p1.firstName, p3.firstName, ok)
	}

}

// TestPeople_Less3 compares by lastname
func TestPeople_Less3(t *testing.T) {
	fmt.Println("TestPeople_Less1 triggered")
	p1 := Person{
		firstName: "Nurlan",
		lastName:  "Ikhsan",
		birthDay:  time.Date(1996, time.Month(1), 15, 0, 0, 0, 0, time.Local),
	}
	p2 := Person{
		firstName: "Nurzhan",
		lastName:  "Ikhsan",
		birthDay:  time.Date(1997, time.Month(12), 7, 0, 0, 0, 0, time.Local),
	}
	p3 := Person{
		firstName: "Nurlan",
		lastName:  "Iskander",
		birthDay:  time.Date(1996, time.Month(1), 15, 0, 0, 0, 0, time.Local),
	}

	people := People{p1, p2, p3}
	indx0 := 0
	indx1 := 2
	ok := people.Less(indx0, indx1)
	if !ok {
		t.Errorf("expected to be %v < %v, but got vice verse: %v", p1.lastName, p3.lastName, ok)
	}

}

func TestPeople_Swap(t *testing.T) {
	fmt.Println("TestPeople_Swap triggered")
	p1 := Person{
		firstName: "Nurlan",
	}
	p2 := Person{firstName: "Nurzhan"}
	p3 := Person{}

	indx0 := 0
	indx1 := 1

	people := People{p1, p2, p3}

	people.Swap(indx0, indx1)

	if people[indx0].firstName != p2.firstName {
		t.Errorf("expected: %s, but got: %s", p2.firstName, people[indx0].firstName)
	}

}

func TestMatrix_Rows(t *testing.T) {
	nbr := "2"

	nm, err := New(nbr)
	if err != nil {
		t.Errorf("got unexpected error: %s", err.Error())
	}

	rr := nm.Rows()

	sx := strings.Split(nbr, "\n")

	rows := len(sx)

	if rows != nm.rows {
		t.Errorf("rows wrong")
	}

	var ns []string
	for _, ss := range sx {
		ns = append(ns, strings.Split(ss, " ")...)
	}

	var i int
	for _, ss := range rr {
		for _, el := range ss {
			if strconv.Itoa(el) != ns[i] {
				t.Errorf("error")
			}
			i++
		}
	}

}

func TestMatrix_Cols(t *testing.T) {

	nbr := "3 3 5"

	nm, err := New(nbr)
	if err != nil {
		t.Errorf("got unexpected error: %s", err.Error())
	}

	sx := strings.Split(nbr, "\n")
	cols := 0

	var ns []string
	for _, ss := range sx {
		sp := strings.Split(ss, " ")
		cols = len(sp)
		ns = append(ns, sp...)
	}

	if cols != nm.cols {
		t.Errorf("cols wrong")
	}

	cc := nm.Cols()

	i := 0
	for _, ss := range cc {
		for _, el := range ss {
			if strconv.Itoa(el) != ns[i] {
				t.Errorf("err")
			}
			i++
		}
	}
}

func TestMatrix_Set(t *testing.T) {
	nbr := "3 3 5\n4 5 6"

	nm, err := New(nbr)
	if err != nil {
		t.Errorf("got unexpected error: %s", err.Error())
	}

	row := 1
	col := 2
	val := 3

	_ = nm.Set(row, col, val)

	sx := strings.Split(nbr, "\n")

	var ns [][]string
	for _, ss := range sx {
		ns = append(ns, strings.Split(ss, " "))
	}

	rr := nm.Rows()

	if len(rr) > row {
		if len(rr[row]) > col {
			if vv := rr[row][col]; vv != val {
				t.Errorf("error val")
			}
		}
	}

}
