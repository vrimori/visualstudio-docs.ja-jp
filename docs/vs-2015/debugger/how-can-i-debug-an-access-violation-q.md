---
title: アクセス違反をデバッグするには | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.access
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
caps.latest.revision: 21
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6c06121d84c6b573b5f1895fa447535826dad540
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540255"
---
# <a name="how-can-i-debug-an-access-violation"></a>アクセス違反をデバッグするには
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[アクセス違反をデバッグする方法でしょうか。](https://docs.microsoft.com/visualstudio/debugger/how-can-i-debug-an-access-violation-q)します。  
  
問題の説明  
 プログラムでアクセス違反が発生します。 どのようにデバッグしたらいいのでしょうか。  
  
## <a name="solution"></a>ソリューション  
 複数のポインターを逆参照するコード行でアクセス違反が発生する場合、どのポインターがアクセス違反を引き起こしたかを見つけるのが困難な場合があります。 Visual Studio 2015 の Update 1 以降、例外ダイアログ ボックスにアクセス違反の原因となったポインターの名前が明示的に表示されるようになりました。  
  
 たとえば、次のコードではアクセス違反が発生します。  
  
```cpp  
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
  
 ポインターがアクセス違反を引き起こした理由を特定できない場合、コードをトレースして、問題の原因となったポインターが正しく割り当てられているかどうかを確認します。  パラメーターとして渡される場合は、正常に渡され、誤って [簡易コピー](http://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)を作成していないことを確認します。 次に、問題のポインターに対してデータ ブレークポイントを作成し、プログラム内の別の場所で変更されていないことを確認することにより、値がプログラム内のどこかで意図せずに変更されていないことを検証します。 データ ブレークポイントの詳細については、 [Using Breakpoints](../debugger/using-breakpoints.md)のデータ ブレークポイントのセクションを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ネイティブ コードのデバッグに関する FAQ](../debugger/debugging-native-code-faqs.md)



