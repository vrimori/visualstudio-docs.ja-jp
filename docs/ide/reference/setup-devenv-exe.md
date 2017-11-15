---
title: "-Setup (devenv.exe) | Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- setup Devenv switch
- /setup Devenv switch
- Devenv, /setup switch
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e63b69c9d97edf5049dfb6e55b8f9d5010984d4d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="setup-devenvexe"></a>/Setup (devenv.exe)
使用できるすべての VSPackages にある、メニュー、ツール バー、およびコマンド グループを記述したリソース メタデータが [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] により強制的にマージされます。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /setup  
```  
  
## <a name="remarks"></a>コメント  
 このスイッチは引数を取りません。 `devenv /setup` コマンドは、一般的にインストール処理の最後の手順として提示されます。 `/setup` スイッチを使用しても、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]は起動しません。  
  
 `devenv` スイッチおよび [devenv](../../ide/reference/setup-devenv-exe.md) スイッチを使用するには、管理者として [devenv](../../ide/reference/installvstemplates-devenv-exe.md) を実行する必要があります。  
  
## <a name="example"></a>例  
 この例は、VSPackages が含まれるバージョンの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のインストールの最後の手順を示しています。  
  
```  
devenv /setup  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)