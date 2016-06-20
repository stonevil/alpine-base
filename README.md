# Description

.

# Containers Schema
	                                                                              
	             ┌─────────────┐                                                  
	             │ alpine:edge │                                                  
	             └─────────────┘                                                  
	  ┌──────┐          │                                                         
	 ─│ BASE ├ ─ ─ ─ ─ ─│─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
	  └──────┘          ▼                                                         
	             ┌─────────────┐   ┌─────────────┐                                
	             │    base     │──▶│    glibc    │──────────┐                     
	             └─────────────┘   └─────────────┘          │                     
	  ┌──────┐                            │                 │                     
	 ─│ Apps ├ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─│─ ─ ─ ─ ─ ─ ─ ─ ─│─ ─ ─ ─ ─ ─ ─ ─ ─ ─ ─
	  └──────┘                            │                 │                     
	                                      ▼                 ▼                     
	                               ┌─────────────┐   ┌─────────────┐              
	                               │     JRE     │   │   NodeJS    │              
	                               └─────────────┘   └─────────────┘              