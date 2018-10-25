---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79a00da92ac2da6eb37fa1eef90fa112598d23f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264961"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
ソリューション ファイルおよびそのすべてのプロジェクト ファイル、または指定されたプロジェクト ファイルを、そのファイルに対応する現在の [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] の形式に更新します。  
  
## <a name="syntax"></a>構文  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>引数  
 `SolutionFile`  
 ソリューションおよびそのプロジェクト全体をアップグレードする場合は必須です。 ソリューション ファイルのパスと名前です。 ソリューション ファイルの名前のみを入力するか、完全パスと名前を入力できます。 存在しないフォルダー名やファイル名を入力した場合は、フォルダーやファイルが作成されます。  
  
 `ProjectFile`  
 単一のプロジェクトをアップグレードする場合、必須です。 ソリューション内のプロジェクト ファイルのパスと名前です。 プロジェクト ファイルの名前のみを入力するか、完全パスと名前を入力できます。 存在しないフォルダー名やファイル名を入力した場合は、フォルダーやファイルが作成されます。  
  
## <a name="remarks"></a>Remarks  
 バックアップは自動的に作成され、現在のディレクトリに作成される Backup という名前のディレクトリにコピーされます。  
  
 ソース管理されたソリューションまたはプロジェクトは、アップグレードする前にチェックアウトする必要があります。  
  
 `/upgrade` スイッチを使用した場合、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] は起動されません。 アップグレードの結果は、ソリューションまたはプロジェクトの開発言語のアップグレード レポートで参照できます。 エラーや使用方法は返されません。 プロジェクトのアップグレードの詳細については[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]を参照してください[方法: トラブルシューティング失敗した Visual Studio プロジェクトのアップグレード](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)します。  
  
## <a name="example"></a>例  
 この例では、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ソリューションの既定フォルダーにある "MyProject.sln" という名前のソリューション ファイルをアップグレードします。  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>関連項目  
 [方法: プロジェクトのアップグレードが失敗した Visual Studio のトラブルシューティング](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Devenv コマンド ライン スイッチ](../../ide/reference/devenv-command-line-switches.md)



