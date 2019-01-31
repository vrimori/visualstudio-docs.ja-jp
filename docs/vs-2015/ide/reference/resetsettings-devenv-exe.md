---
title: -ResetSettings (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /ResetSettings switch
- ResetSettings switch
- /ResetSettings Devenv switch
ms.assetid: 1d41021c-6f58-4bd5-b122-d1c995812192
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 60e0dd272bd22cce2367e59b16fdea7965cb50e7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54761590"
---
# <a name="resetsettings-devenvexe"></a>/ResetSettings (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の既定の設定を復元し、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE を自動的に開始します。 指定の .vssettings ファイルに準じた設定にリセットすることもできます。  
  
 既定の設定は、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の初回起動時に選択したプロファイルによって決定されます。  
  
## <a name="syntax"></a>構文  
  
```  
Devenv /ResetSettings SettingsFile  
```  
  
## <a name="arguments"></a>引数  
 `SettingsFile`  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] に適用する .vssettings ファイルの完全パスとファイル名です。  
  
 全般的な開発設定のプロファイルを復元するには、`General` を使用します。  
  
## <a name="remarks"></a>コメント  
 `SettingsFile` が指定されていない場合、次回 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] を起動したときに、既定の設定のコレクションを選択するよう要求されます。  
  
## <a name="example"></a>例  
 `MySettings.vssettings` ファイルに保存された設定を適用するコマンド ラインを次に示します。  
  
```  
Devenv.exe /ResetSettings "C:\My Files\MySettings.vssettings"  
```  
  
## <a name="see-also"></a>「  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)
