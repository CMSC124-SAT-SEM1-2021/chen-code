# Syntax Exercise
### CMSC 124 SAT | Fernandez, Chien Carisse P.

* #### Create a grammar for a small language using BNF that accepts a program code that (1) starts with the special word *begin*, (2) followed by one or more assignment statements, wherein each statement ends with a semicolon (use the BNF for assignment in the example at the parse tree section), (3) after the last statement, the code should end with the special word *end*
``` 
<statement-sequence> -> begin <statement-sequence> end | begin <statement> <statement-sequence> end
<statement> -> <statement> ; | <statement> <assign> ; | <assign>;
<assign> -> <var> = <expr>
<expr> -> <expr> | <expr> + <expr> | <expr> * <expr> | <var> + <var> | <var> * <var> | ( <expr>) | <var> * <expr> | <var> + <expr>
<var> -> A | B | C

```
* #### Derive the statement below and create a parse tree for it:
	 begin B = C * A + B * B; C = (B * C + A); end
     
     * #### **Derivation of the statement:**
     ```
      <statement-sequence> -> begin <statement> end
                    -> begin <statement> <assignment> ; end
                    -> begin <assign> ; <assign> ; end
                    -> begin <var> = <expr> ; <assign> ; end
                    -> begin B = <expr> ; <assign> ; end
                    -> begin B = <expr> + <expr> ; <assign> ; end
                    -> begin B = <var> * <expr> + <var> * <expr> ; <assign> ; end
                    -> begin B = <var> * <var> + <var> * <var> ; <assign> ; end
                    -> begin B = C * <var> + <var> * <var> ; <assign> ; end
                    -> begin B = C * A + <var> * <var> ; <assign> ; end
                    -> begin B = C * A + B * <var> ; <assign> ; end
                    -> begin B = C * A + B * B ; <assign> ; end
                    -> begin B = C * A + B * B ; <var> = <expr> ; end
                    -> begin B = C * A + B * B ; C = <expr> ; end
                    -> begin B = C * A + B * B ; C = (<expr>) ; end
                    -> begin B = C * A + B * B ; C = (<var> * <expr>) ; end
                    -> begin B = C * A + B * B ; C = (B * <expr>) ; end
                    -> begin B = C * A + B * B ; C = (B * <var> + <expr>) ; end
                    -> begin B = C * A + B * B ; C = (B * <var> + <var>) ; end
                    -> begin B = C * A + B * B ; C = (B * C + <var>) ; end
                    -> begin B = C * A + B * B ; C = (B * C + A) ; end
     ```

    * #### **Parse Tree**
    #### If the image cannot be displayed, parse tree image is on this [link](https://drive.google.com/file/d/1iqLPfg0b3KPyt691mMlcADKn9i4D4MB4/view?usp=sharing).
    <iframe src="https://drive.google.com/file/d/1iqLPfg0b3KPyt691mMlcADKn9i4D4MB4/preview" width="640" height="480" allow="autoplay"></iframe>