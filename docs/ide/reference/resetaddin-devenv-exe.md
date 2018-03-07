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
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 36b003f4890b16a7b69f7f66f8b0ef83a0ade7ac
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
コマンドおよび指定されたアドインに関連付けられたコマンド UI を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>引数  
 `AddIn`  
 任意。 アドインのコマンド名。  
  
## <a name="remarks"></a>コメント  
 既定では、アドインのコマンド名は *\<AddInSolutionName>*.Connect*.\<AddInSolutionName>* と同じで、Connect.cs では `Exec` メソッドの `commandName` パラメーターとして表示されます。 また、Visual Studio のコマンド ウィンドウでアドインの名前を途中まで入力し、IntelliSense を使用して残りを自動的に表示させることでコマンド名を確認することもできます。  
  
## <a name="example"></a>例  
 次の例は、Visual Studio を起動して、`MyAddin` アドインを起動時に実行しないようにします。  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)