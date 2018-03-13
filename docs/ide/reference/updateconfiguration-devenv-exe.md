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
caps.latest.revision: 
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 0ec3bfc47829bce2fe5ad836c970cb28f8a1294e
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2018
---
# <a name="updateconfiguration-devenvexe"></a>/Updateconfiguration (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] にシステム上の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージをマージさせ、MEF キャッシュに変更がないかを確認することを通知します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /updateconfiguration  
```  
  
## <a name="remarks"></a>コメント  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSIX パッケージをインストールすると、 ではこのコマンドが自動的に実行されます。 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] が MEF キャッシュを更新するように、ファイルの修正プログラムを適用した後に `devenv.exe /updateconfiguration` を実行する必要があります。 これにより、修正が適切かどうかを評価することができます。  
  
## <a name="example"></a>例  
 次のコマンド ラインでは、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] にシステム上の [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージをマージさせ、MEF キャッシュに変更がないかを確認させます。  
  
```  
Devenv.exe /updateconfiguration  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)