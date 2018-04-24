---
title: '[国際対応の設定] ([オプション] ダイアログ ボックス - [環境]) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Environment.InternationalSettings
- VS.ToolsOptionsPages.Environment.International_Settings
- VS.Environment.International Settings
- VS.ToolsOptionsPag.Environment.International_Settings
helpviewer_keywords:
- International Settings dialog box
- languages, environment settings
- Options dialog box, international settings
- languages, specifying default
ms.assetid: e3a8815c-6995-4099-8e88-34f91fad55b2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 33e206e4c38b4bde715d72c6b8eb4b5bdf9c5dd8
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="international-settings-environment-options-dialog-box"></a>[国際対応の設定] \([オプション] ダイアログ ボックス - [環境])
コンピューターにインストールされている統合開発環境 (IDE) に複数の言語バージョンがある場合は、[国際対応の設定] ページで既定の言語を変更できます。 このダイアログ ボックスにアクセスするには、**[ツール]** メニューの **[オプション]** を選択し、**[環境]** フォルダーから **[国際対応の設定]** を選択します。 このページが一覧に表示されない場合は、**[オプション]** ダイアログ ボックスの **[すべての設定を表示]** を選択します。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 **Language**  
 インストールされている製品の言語バージョンで使用可能な言語の一覧が表示されます。 コンピューターに複数の言語バージョンがインストールされていない場合、このオプションは使用できません。 複数言語の製品または混合言語の製品で環境を共有する場合は、言語の選択が **[Microsoft Windows と同じ]** に変更されます。  
  
> [!CAUTION]
>  複数の言語がインストールされているシステムでは、Visual C++ ビルド ツール (cl.exe、link.exe、nmake.exe、bscmake.exe、および関連ファイル) はこの設定による影響を受けません。 これらのツールでは、最後にインストールされた言語のバージョンを使用します。 Visual C++ ビルド ツールはサテライト DLL モデルを使用しないため、以前にインストールされた言語のビルド ツールは上書きされます。  
  
## <a name="see-also"></a>参照  
 [言語パックのインストール](../../install/install-visual-studio.md#step-6---install-language-packs-optional)   
 [[環境] ([オプション] ダイアログ ボックス)](../../ide/reference/environment-options-dialog-box.md)