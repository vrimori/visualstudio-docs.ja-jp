---
title: '[設定のインポートとエクスポート] コマンド | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: b6b29179332920197960ebe3be71e5973bdc8fe9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769452"
---
# <a name="import-and-export-settings-command"></a>[設定のインポートとエクスポート] コマンド
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の設定をインポート、エクスポート、またはリセットします。  
  
## <a name="syntax"></a>構文  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>スイッチ  
 /export:`filename`  
 任意。 現在の設定を指定したファイルにエクスポートします。  
  
 /import:`filename`  
 任意。 設定を指定したファイルからインポートします。  
  
 /reset  
 任意。 現在の設定をリセットします。  
  
## <a name="remarks"></a>コメント  
 スイッチを指定しないでこのコマンドを実行すると、**[設定のインポートとエクスポート]** ウィザードが開きます。 詳細については、「[方法 :コンピューターまたは Visual Studio のバージョン間の設定を共有](http://msdn.microsoft.com/1131fb10-35c1-42da-9cd8-91aa3235b882)します。  
  
## <a name="example"></a>例  
 次のコマンドは、現在の設定を `MyFile.vssettings` ファイルにエクスポートします。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>「  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
