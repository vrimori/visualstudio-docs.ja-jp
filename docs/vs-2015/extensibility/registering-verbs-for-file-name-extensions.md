---
title: ファイル名拡張子の動詞を登録する |Microsoft Docs
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
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d81916910eb4769801ae330c10edde24cb52f52
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2018
ms.locfileid: "49923408"
---
# <a name="registering-verbs-for-file-name-extensions"></a>ファイル名拡張子の動詞を登録する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

アプリケーションとファイル名拡張子の関連付けは、通常、ユーザーがファイルをダブルクリックしたときに発生する推奨アクションを持っています。 これは、アクションは、動詞、たとえばオープン操作に対応するにリンクさせます (推奨)。  
  
 HKEY_CLASSES_ROOT にあるシェルのキーを使用して、拡張機能のプログラム識別子 (ProgID) に関連付けられている動詞を登録する\\*progid*\shell します。 詳細については、次を参照してください。[ファイルの種類](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)します。  
  
## <a name="registering-standard-verbs"></a>標準的な動詞を登録します。  
 オペレーティング システムでは、次の標準的な動詞を認識します。  
  
- 開く  
  
- 編集  
  
- 再生  
  
- の  
  
- [プレビュー]  
  
  可能であれば、標準的な動詞を登録します。 最も一般的な選択肢では、Open 動詞です。 ファイルを開くと、ファイルの編集の間の明確な違いがある場合にのみ編集動詞を使用します。 たとえば、.htm のファイルを開くに表示されます、ブラウザーは HTML エディターが起動 .htm ファイルを編集します。 標準的な動詞は、オペレーティング システムのロケールでローカライズされます。  
  
> [!NOTE]
>  標準的な動詞を登録するときに、開いているキーの既定値を設定しないでください。 既定値には、メニューの表示文字列が含まれています。 オペレーティング システムでは、標準的な動詞にこの文字列を提供します。  
  
 新しいインスタンスを起動するプロジェクト ファイルを登録する必要があります[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]ときに、ユーザーがファイルを開きます。 次の例では、標準の動詞の登録、[!INCLUDE[csprcs](../includes/csprcs-md.md)]プロジェクト。  
  
```  
[HKEY_CLASSES_ROOT\.csproj]  
@="VisualStudio.csproj.8.0"  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList]  
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]  
"VisualStudio.csproj.8.0"=""  
  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]  
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]  
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]  
@="C# Project file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]  
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""  
```  
  
 既存のインスタンスでファイルを開く[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]、DDEEXEC キーを登録します。 次の例では、標準の動詞の登録、 [!INCLUDE[csprcs](../includes/csprcs-md.md)] .cs ファイルです。  
  
```  
[HKEY_CLASSES_ROOT\.cs]  
@="VisualStudio.cs.8.0"  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithList]  
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]  
@=""  
  
[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]  
"VisualStudio.cs.8.0"=""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]  
@="C# Source file"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]  
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]  
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]  
@="Open(\"%1\")"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]  
@="VisualStudio.8.0"  
  
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]  
@="system"  
```  
  
## <a name="setting-the-default-verb"></a>既定の動詞の設定  
 既定の動詞は、ユーザーが Windows エクスプ ローラーでファイルをダブルクリックしたときに実行されるアクションです。 既定の動詞は、HKEY_CLASSES_ROOT の既定値として指定された動詞\\*progid*\Shell キー。 値が指定されていない場合、既定の動詞は、HKEY_CLASSES_ROOT に指定された最初の動詞を\\*progid*\Shell キーのリスト。  
  
> [!NOTE]
>  サイド バイ サイドで配置の拡張機能の既定の動詞を変更する場合は、インストールと削除の影響を検討してください。 インストール中に、元の既定値は上書きされます。  
  
## <a name="see-also"></a>関連項目  
 [side-by-side のファイルの関連付けを管理する](../extensibility/managing-side-by-side-file-associations.md)

