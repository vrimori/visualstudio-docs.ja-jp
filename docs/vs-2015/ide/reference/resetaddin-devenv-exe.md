---
title: -ResetAddin (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f1b53a30845ca4b20372fb5a6e3552f31f3c1b60
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49950525"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
コマンドおよび指定されたアドインに関連付けられたコマンド UI を削除します。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>引数  
 `AddIn`  
 任意。 アドインのコマンド名。  
  
## <a name="remarks"></a>Remarks  
 既定では、アドインのコマンド名は *\<AddInSolutionName>*.Connect<em>.\<AddInSolutionName></em> と同じで、Connect.cs では `Exec` メソッドの `commandName` パラメーターとして表示されます。 また、Visual Studio のコマンド ウィンドウでアドインの名前を途中まで入力し、IntelliSense を使用して残りを自動的に表示させることでコマンド名を確認することもできます。  
  
## <a name="example"></a>例  
 次の例は、Visual Studio を起動して、`MyAddin` アドインを起動時に実行しないようにします。  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



