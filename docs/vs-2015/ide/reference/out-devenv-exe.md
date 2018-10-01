---
title: -Out (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4edcdf6da73c3f4c4ee9d221d7bbaef8e520c5e3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540263"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[-(devenv.exe) アウト](https://docs.microsoft.com/visualstudio/ide/reference/out-devenv-exe)します。  
  
  
ソリューションを実行、ビルド、リビルド、または配置したときに、エラーを格納し表示するファイルを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv /out FileName  
```  
  
## <a name="arguments"></a>引数  
 `FileName`  
 必須。 実行可能ファイルのビルド時にエラーを受け取るファイルのパスと名前です。  
  
## <a name="remarks"></a>Remarks  
 指定したファイル名が存在しない場合は、自動的に作成されます。 ファイルが既に存在する場合、結果はファイルの既存の内容に追加されます。  
  
 コマンド ラインのビルド エラーは、**[コマンド]** ウィンドウと **[出力]** ウィンドウの [ソリューション ビルダー] ビューに表示されます。 このオプションは、無人操作でビルドを実行して結果を表示する必要がある場合に便利です。  
  
## <a name="example"></a>例  
 次の例では、`MySolution` を実行し、エラーをファイル `MyErrorLog.txt` に書き込みます。  
  
```  
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"  
```  
  
## <a name="see-also"></a>関連項目  
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)   
 [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)   
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)



