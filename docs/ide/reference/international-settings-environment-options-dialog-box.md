---
title: "[国際対応の設定] ([オプション] ダイアログ ボックス - [環境]) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 14
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: b92985ecd674fe750504c3aa85634b8c09fcdd5a
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="international-settings-environment-options-dialog-box"></a>[国際対応の設定] ([オプション] ダイアログ ボックス - [環境])
コンピューターにインストールされている統合開発環境 (IDE) に複数の言語バージョンがある場合は、[国際対応の設定] ページで既定の言語を変更できます。 このダイアログ ボックスにアクセスするには、**[ツール]** メニューの **[オプション]** を選択し、**[環境]** フォルダーから **[国際対応の設定]** を選択します。 このページが一覧に表示されない場合は、**[オプション]** ダイアログ ボックスの **[すべての設定を表示]** を選択します。  
  
> [!NOTE]
>  使用している設定またはエディションによっては、ダイアログ ボックスで使用可能なオプションや、メニュー コマンドの名前や位置がヘルプに記載されている内容と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)」を参照してください。  
  
 **言語**  
 インストールされている製品の言語バージョンで使用可能な言語の一覧が表示されます。 コンピューターに複数の言語バージョンがインストールされていない場合、このオプションは使用できません。 複数言語の製品または混合言語の製品で環境を共有する場合は、言語の選択が **[Microsoft Windows と同じ]** に変更されます。  
  
> [!CAUTION]
>  複数の言語がインストールされているシステムでは、Visual C++ ビルド ツール (cl.exe、link.exe、nmake.exe、bscmake.exe、および関連ファイル) はこの設定による影響を受けません。 Visual C++ ビルド ツールはサテライト DLL モデルを使用しないため、これらのツールは最後にインストールされた言語のバージョンを使用し、以前にインストールされた言語のツールは上書きされます。  
  
## <a name="see-also"></a>関連項目  
 [言語パックのインストール](../../install/install-visual-studio.md#install-language-packs)   
 [[環境] ([オプション] ダイアログ ボックス)](../../ide/reference/environment-options-dialog-box.md)
