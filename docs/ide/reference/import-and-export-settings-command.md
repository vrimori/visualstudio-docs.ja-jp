---
title: '[設定のインポートとエクスポート] コマンド'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
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
ms.openlocfilehash: a95841d9b9b8e67f34883efcc1a55a2daba7e8b7
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
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

- [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)
- [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)