---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 741deb2d7ddb86e0a0dc0246b1c53f497d0ab5f8

---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] にシステム上の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージをマージさせ、MEF キャッシュに変更がないかを確認することを通知します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>コメント  
 VSIX パッケージをインストールすると、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ではこのコマンドが自動的に実行されます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が MEF キャッシュを更新するように、ファイルの修正プログラムを適用した後に `devenv.exe /updateconfiguration` を実行する必要があります。 これにより、修正が適切かどうかを評価することができます。  
  
## <a name="example"></a>例  
 次のコマンド ラインでは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] にシステム上の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージをマージさせ、MEF キャッシュに変更がないかを確認させます。  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)


<!--HONumber=Feb17_HO4-->


