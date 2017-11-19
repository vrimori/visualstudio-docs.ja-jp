---
title: "C++ アクセス違反をデバッグする方法は? | Microsoft Docs"
ms.custom: 
ms.date: 05/23/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: "18"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93b7a670d74fbbb0c9d8e13f1e6463b52a8ca5d2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-debug-a-c-access-violation"></a>C++ アクセス違反をデバッグする方法は?
## <a name="problem-description"></a>問題の説明  
 プログラムでアクセス違反が発生します。 どのようにデバッグしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 複数のポインターを逆参照するコード行でアクセス違反が発生する場合、どのポインターがアクセス違反を引き起こしたかを見つけるのが困難な場合があります。 Visual Studio 2015 の Update 1 以降、例外ダイアログ ボックスにアクセス違反の原因となったポインターの名前が明示的に表示されるようになりました。  
  
 たとえば、次のコードではアクセス違反が発生します。  
  
```C++  
#include <iostream>  
using namespace std;  
  
class ClassB {  
public:  
        ClassC* C;  
        ClassB() {  
                C = new ClassC();  
        }  
     void printHello() {  
                cout << "hello world";  
        }  
};  
  
class ClassA {  
public:  
    ClassB* B;  
      ClassA() {  
                B = nullptr;  
        }  
};  
  
int main() {  
    ClassA* A = new ClassA();  
      A->B->printHello();  
}  
```  
  
 このコードを Visual Studio 2015 の Update 1 で実行する場合、次の例外ダイアログ ボックスが表示されます。  
  
 ![AccessViolationCPlus](../debugger/media/accessviolationcplus.png "AccessViolationCPlus")  
  
 ポインターがアクセス違反を引き起こした理由を特定できない場合、コードをトレースして、問題の原因となったポインターが正しく割り当てられているかどうかを確認します。  場合は、パラメーターとして渡される、正しく、渡され、誤ってを作成していないことを確認する、[コピーの浅い](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)です。 値が変更されないことされている意図せずどこかに、プログラムでは、プログラムで別の場所で変更されていないかどうかを確認する対象のポインターに対してデータ ブレークポイントを作成して、確認します。 データ ブレークポイントの詳細については、 [Using Breakpoints](../debugger/using-breakpoints.md)のデータ ブレークポイントのセクションを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)