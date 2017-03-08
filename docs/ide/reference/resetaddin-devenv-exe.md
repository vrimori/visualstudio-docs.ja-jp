---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 5
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: cfc96ba712fbc057f9e6e57c61c80ebe38bd662c
ms.lasthandoff: 02/22/2017

---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
コマンドおよび指定されたアドインに関連付けられたコマンド UI を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>引数  
 `AddIn`  
 省略可能です。 アドインのコマンド名。  
  
## <a name="remarks"></a>コメント  
 既定では、アドインのコマンド名は *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>* と同じで、Connect.cs では `Exec` メソッドの `commandName` パラメーターとして表示されます。 また、Visual Studio のコマンド ウィンドウでアドインの名前を途中まで入力し、IntelliSense を使用して残りを自動的に表示させることでコマンド名を確認することもできます。  
  
## <a name="example"></a>例  
 次の例は、Visual Studio を起動して、`MyAddin` アドインを起動時に実行しないようにします。  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
