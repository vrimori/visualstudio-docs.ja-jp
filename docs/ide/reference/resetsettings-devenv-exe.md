---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52d01cfc3ae6a453330c2dda5da137f449ff5cbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の既定の設定を復元し、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE を自動的に開始します。 指定の .vssettings ファイルに準じた設定にリセットすることもできます。  
  
 既定の設定は、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の初回起動時に選択したプロファイルによって決定されます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>引数  
 `SettingsFile`  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に適用する .vssettings ファイルの完全パスとファイル名です。  
  
 全般的な開発設定のプロファイルを復元するには、`General` を使用します。  
  
## <a name="remarks"></a>コメント  
 `SettingsFile` が指定されていない場合、次回 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を起動したときに、既定の設定のコレクションを選択するよう要求されます。  
  
## <a name="example"></a>例  
 `MySettings.vssettings` ファイルに保存された設定を適用するコマンド ラインを次に示します。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>参照  
 [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)