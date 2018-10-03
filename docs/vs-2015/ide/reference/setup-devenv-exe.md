---
title: -Setup (devenv.exe) | Microsoft ドキュメント
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
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75b7fb7d812135014a8b868ef7590c99e83c15b5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47544513"
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[-セットアップ (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/setup-devenv-exe)します。  
  
  
使用できるすべての VSPackages にある、メニュー、ツール バー、およびコマンド グループを記述したリソース メタデータが [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] により強制的にマージされます。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>Remarks  
 このスイッチは引数を取りません。 `devenv /setup` コマンドは、一般的にインストール処理の最後の手順として提示されます。 `/setup` スイッチを使用しても、 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]は起動しません。  
  
 `devenv` スイッチおよび [devenv](../../ide/reference/setup-devenv-exe.md) スイッチを使用するには、管理者として [devenv](../../ide/reference/installvstemplates-devenv-exe.md) を実行する必要があります。  
  
## <a name="example"></a>例  
 この例は、VSPackages が含まれるバージョンの [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] のインストールの最後の手順を示しています。  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



