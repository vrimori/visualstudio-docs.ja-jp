---
title: -Updateconfiguration (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /updateconfiguration Devenv switch
- Devenv, /updateconfiguration switch
- updateconfiguration Devenv switch
ms.assetid: 9a1084cc-8b68-4ccc-aaea-f95939164338
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 31fd7f52ad2be89a3e6a40a76948aea0d8cc8bfc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47537420"
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[Updateconfiguration (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/updateconfiguration-devenv-exe)します。  
  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] にシステム上の [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] パッケージをマージさせ、MEF キャッシュに変更がないかを確認することを通知します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>Remarks  
 VSIX パッケージをインストールすると、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ではこのコマンドが自動的に実行されます。 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] が MEF キャッシュを更新するように、ファイルの修正プログラムを適用した後に `devenv.exe /updateconfiguration` を実行する必要があります。 これにより、修正が適切かどうかを評価することができます。  
  
## <a name="example"></a>例  
 次のコマンド ラインでは、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] にシステム上の [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] パッケージをマージさせ、MEF キャッシュに変更がないかを確認させます。  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



