---
title: -SafeMode (devenv.exe) | Microsoft Docs
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
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 308dd7e81a35604bcd0f6f5eba517b850ace17ad
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47539903"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[/safemode (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/safemode-devenv-exe)します。  
  
  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] をセーフ モードで起動し、既定の環境とサービスのみを読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /SafeMode   
```  
  
## <a name="remarks"></a>Remarks  
 このスイッチでは、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] が起動したときに、すべてのサード パーティ VSPackage を読み込まないようにするため、実行が安定したものになります。  
  
## <a name="description"></a>説明  
 次の例では、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] をセーフ モードで起動します。  
  
## <a name="code"></a>コード  
  
```  
Devenv.exe /SafeMode  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



