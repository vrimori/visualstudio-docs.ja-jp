---
title: CreatePkgDef ユーティリティ |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63334ba9d454407bb93a87bf89b12cb472184d58
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/12/2018
ms.locfileid: "49181598"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef ユーティリティ
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

パラメーターとして Visual Studio 拡張機能の .dll ファイルを受け取り、.dll に付随する .pkgdef ファイルを作成します。 .Pkgdef ファイルには、拡張機能がインストールされている場合、システム レジストリに書き込まそれ以外の場合は、すべての情報が含まれています。  
  
> [!NOTE]
>  自動的に Visual Studio SDK に含まれるプロジェクト テンプレートのほとんどは、ビルド プロセスの一環として、.pkgdef ファイルを作成します。 このドキュメントはパッケージを手動で作成または .pkgdef 展開を使用する既存のパッケージを変換する必要がある場合を対象としています。  
  
## <a name="syntax"></a>構文  
  
```  
CreatePkgDef /out=FileName [/codebase] [/assembly] AssemblyPath  
```  
  
## <a name="arguments"></a>引数  
 /アウト =`FileName`  
 必須。 .Pkgdef 出力ファイルの名前を設定`FileName`します。  
  
 /codebase  
 任意。 コードベースのユーティリティを使用して強制的に登録します。  
  
 /assembly  
 アセンブリ ユーティリティを使用して強制的に登録します。  
  
 `AssemblyPath`  
 .Pkgdef を生成する .dll ファイルのパス。  
  
## <a name="remarks"></a>Remarks  
 .Pkgdef ファイルを使用して拡張機能の配置には、Visual Studio の以前のバージョンのレジストリの要件が置き換えられます。  
  
 .Pkgdef ファイルは、次の場所のいずれかでインストールする必要があります: %localappdata%\Microsoft\Visual Studio\14.0\Extensions\ または %vsinstalldir%\Common7\IDE\Extensions\\します。 インストール フォルダーは、%localappdata%\Microsoft\Visual Studio\14.0\Extensions 場合\\、拡張機能は、Visual Studio によって認識されますは既定で無効になります。 ユーザーを使用して、拡張機能を有効にできます**拡張機能と更新**します。 インストール フォルダーは、%vsinstalldir%\Common7\IDE\Extensions 場合\\、拡張機能が既定で有効にします。  
  
> [!NOTE]
>  **拡張機能と更新**ツールは VSIX パッケージの一部としてインストールされていない場合、拡張機能へのアクセスに使用できません。  
  
## <a name="see-also"></a>関連項目  
 [CreateExpInstance ユーティリティ](../../extensibility/internals/createexpinstance-utility.md)

