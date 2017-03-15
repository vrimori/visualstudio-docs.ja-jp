---
title: "__pin | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__pin"
  - "__pin_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "固定ポインター、_ _pin キーワード"
  - "アンマネージ型"
  - "__pin キーワード"
ms.assetid: 8b55c792-5654-4669-bb0e-a52100f4cabe
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# __pin
メモ   このトピックは、C\+\+ マネージ拡張のバージョン 1 にのみ対応しています。 この構文は、バージョン 1 のコードを保守するためだけに使用してください。 参照してください [pin\_ptr \(C\+\+\/CLI\)](/visual-cpp/windows/pin-ptr-cpp-cli) については、新しい構文で同等の機能を使用します。  
  
 ガベージ コレクションの実行中に、共通言語ランタイムによってマネージ クラスのオブジェクトまたは埋め込みオブジェクトが移動されることを防止します。  
  
## 構文  
  
```  
  
__pin   
identifier  
  
```  
  
## 解説  
 `__pin` キーワードは、マネージ クラスのオブジェクトまたは埋め込みオブジェクトへのポインターを宣言し、そのオブジェクトが共通言語ランタイムによるガベージ コレクションの実行中に移動されることを防止します。 これは、アンマネージ関数呼び出しの解決時にアドレスが予想外に変更されることがないため、マネージ クラスのアドレスをアンマネージ関数に渡す場合に便利です。  
  
 固定ポインターは、構文のスコープに有効です。 固定ポインターがスコープ外に出るとすぐに、オブジェクトは固定されているとは見なされなくなります \(もちろん、オブジェクトを指す他の固定ポインターがない場合\)。  
  
 MSIL には「ブロック スコープ」の概念はありません。すべてのローカル変数は関数のスコープ内にあります。 固定が有効でなくなったことをシステムに通知するために、コンパイラは、固定ポインターに null を割り当てるコードを生成します。 これも、ブロックを離れずにオブジェクトの固定を解除する必要がある場合は、自分で行うことができます。  
  
 アンマネージ ポインターに変換して、そのアンマネージ ポインターを、オブジェクトが既に固定されなくなった \(固定ポインターがスコープ外になった\) 後まで使用し続けないでください。 gc ポインターとは異なり、固定ポインターは nogc \(アンマネージ ポインター\) に変換できます。 ただし、ユーザーがアンマネージ ポインターの使用中に固定を維持する必要があります。  
  
 固定されたポインターを使用して変数のアドレスを取得し、固定ポインターがスコープ外になった後でそのアドレスを使用することは、行わないでください。  
  
```  
// keyword_pin_scope_bad.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int* Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return px;   // BE CAREFUL px goes of scope,   
                // so object pointed by it is no longer pinned,  
                // making the return value unsafe.  
}  
```  
  
 次のサンプルは正しい動作を示します。  
  
```  
// keyword_pin_scope_good.cpp  
// compile with: /clr:oldSyntax /LD  
#using <mscorlib.dll>  
__gc struct X {  
   int x;  
};  
  
int Get_x( X* pX ) {  
   int __pin* px = &pX -> x;  
   return *px;   // OK, value obtained from px before px out of scope  
}  
```  
  
## 使用例  
 次の例では、`pG` が指すオブジェクトがスコープ外になるまで固定されます。  
  
```  
// keyword__pin.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
#include <iostream>  
  
__gc class G {   
public:   
   int i;   
   G() {i = 0;};  
};  
  
class H {  
public:  
   // unmanaged function  
   void incr(int * i) {  
      (*i)++;   
      std::cout << *i << std::endl;  
   };  
};  
  
int main() {  
   G __pin * pG = new G;  // pG is a pinning pointer  
   H * h = new H;  
   // pointer to managed data passed as actual parameter of unmanaged   
   // function call  
   h->incr(& pG -> i);   
}  
```  
  
## 出力  
  
```  
1  
```