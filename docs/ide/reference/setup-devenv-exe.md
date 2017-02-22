---
title: "-Setup (devenv.exe) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "setup Devenv スイッチ"
  - "/setup Devenv スイッチ"
  - "Devenv, /setup スイッチ"
ms.assetid: 87608b7f-a156-400c-80f5-fc823f843e61
caps.latest.revision: 14
caps.handback.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# /Setup (devenv.exe)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

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