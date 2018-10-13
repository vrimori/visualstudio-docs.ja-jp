---
title: '[設定のインポートとエクスポート] コマンド | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Tools.ImportandExportSettings
helpviewer_keywords:
- Tools.ImportandExportSettings
- Import and Export Settings command
ms.assetid: 94a06468-a44d-403d-a931-77bbc9d06e56
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2556b814059a80f2b93d0220de27cdbd8c051ea9
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49305566"
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
  
## <a name="remarks"></a>Remarks  
 スイッチを指定しないでこのコマンドを実行すると、**[設定のインポートとエクスポート]** ウィザードが開きます。 詳しくは、「[方法: コンピューター間または Visual Studio のバージョン間で設定を共有する](http://msdn.microsoft.com/en-us/1131fb10-35c1-42da-9cd8-91aa3235b882)」をご覧ください。  
  
## <a name="example"></a>例  
 次のコマンドは、現在の設定を `MyFile.vssettings` ファイルにエクスポートします。  
  
```  
Tools.ImportandExportSettings /export:"c:\Files\MyFile.vssettings"  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Visual Studio のコマンド](../../ide/reference/visual-studio-commands.md)



