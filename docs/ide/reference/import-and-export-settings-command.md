---
title: "[設定のインポートとエクスポート] コマンド | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 5
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
ms.openlocfilehash: dca11a81e650f0470c891cb79623f9cc088ea669
ms.contentlocale: ja-jp
ms.lasthandoff: 05/24/2017

---
# <a name="import-and-export-settings-command"></a>[設定のインポートとエクスポート] コマンド
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の設定をインポート、エクスポート、またはリセットします。  
  
## <a name="syntax"></a>構文  
  
```  
Tools.ImportandExportSettings [/export:filename | /import:filename | /reset]  
```  
  
## <a name="switches"></a>スイッチ  
 /export:`filename`  
 省略可能です。 現在の設定を指定したファイルにエクスポートします。  
  
 /import:`filename`  
 省略可能です。 設定を指定したファイルからインポートします。  
  
 /reset  
 省略可能です。 現在の設定をリセットします。  
  
## <a name="remarks"></a>コメント  
 スイッチを指定しないでこのコマンドを実行すると、**[設定のインポートとエクスポート]** ウィザードが開きます。 詳しくは、「[方法: コンピューター間または Visual Studio のバージョン間で設定を共有する](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコマンドは、現在の設定を `MyFile.vssettings` ファイルにエクスポートします。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio IDE のカスタマイズ](../../ide/personalizing-the-visual-studio-ide.md)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)
