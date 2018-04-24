---
title: '[設定のインポートとエクスポート] コマンド | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ad7da7f8d83cd45e7cc7801d430dbf70887747b3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="import-and-export-settings-command"></a>[設定のインポートとエクスポート] コマンド
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の設定をインポート、エクスポート、またはリセットします。  
  
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

スイッチを指定しないでこのコマンドを実行すると、**[設定のインポートとエクスポート]** ウィザードが開きます。 詳細については、「[同期された設定](../../ide/synchronized-settings-in-visual-studio.md)」を参照してください。

## <a name="example"></a>例

次のコマンドは、現在の設定を `MyFile.vssettings` ファイルにエクスポートします。

```shell
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"
```

## <a name="see-also"></a>関連項目

[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)  
[Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)