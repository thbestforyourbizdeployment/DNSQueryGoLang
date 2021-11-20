# DNSQueryGoLang
#Basic DNS Query in Golang 

package main

import (
	"fmt"
	"net"
)

func main() {

	fmt.Println("EnterDomainName: ")

	// var then variable name then variable type
	var domain string

	// Taking input from user
	fmt.Scanln(&domain)

	iprecords, _ := net.LookupIP(domain)
	for _, ip := range iprecords {
		fmt.Println(ip)
	}

	mxrecords, _ := net.LookupMX(domain)
	for _, mx := range mxrecords {
		fmt.Println(mx.Host, mx.Pref)
	}

	txtrecords, _ := net.LookupTXT(domain)

	for _, txt := range txtrecords {
		fmt.Println(txt)
	}

	nameserver, _ := net.LookupNS(domain)
	for _, ns := range nameserver {
		fmt.Println(ns)
	}
}
