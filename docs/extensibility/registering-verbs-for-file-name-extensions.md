---
title: "ファイル名拡張子の動詞を登録する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8f430486c613e6281404110d4441d2a3d2100534
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="registering-verbs-for-file-name-extensions"></a>ファイル名拡張子の動詞を登録します。
アプリケーションとファイル名拡張子の関連付けは通常、ユーザーがファイルをダブルクリックしたときに発生する推奨されるアクションを持っています。 これを優先する動詞をたとえば開いているアクションに対応するアクションをリンクします。  
  
 HKEY_CLASSES_ROOT であるシェル キーを使用して、拡張機能のプログラム識別子 (ProgID) に関連付けられている動詞を登録する\\*progid*\shell です。 詳細については、次を参照してください。[ファイルの種類](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx)です。  
  
## <a name="registering-standard-verbs"></a>標準的な動詞を登録します。  
 オペレーティング システムには、次の標準的な動詞が認識されます。  
  
-   開く  
  
-   編集  
  
-   再生  
  
-   の  
  
-   [プレビュー]  
  
 可能な限り、標準の動詞を登録します。 最も一般的な選択肢は、Open 動詞です。 ファイルを開くと、ファイルの編集の間で明確な違いがある場合にのみ編集動詞を使用します。 たとえば、.htm のファイルを開くが表示されますが、ブラウザーで、HTML エディターが起動 .htm ファイルを編集します。 標準的な動詞は、オペレーティング システムのロケールでローカライズされます。  
  
> [!NOTE]
>  標準的な動詞を登録するときに、開いているキーの既定値を設定することはしません。 既定値には、メニューの表示文字列が含まれています。 オペレーティング システムでは、標準の verb この文字列を指定します。  
  
 新しいインスタンスを起動するプロジェクト ファイルを登録する必要があります[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ユーザーがファイルを開くとします。 次の例では、標準的な動詞登録を[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]プロジェクト。  
  
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
  
 既存のインスタンスでファイルを開く[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]、DDEEXEC キーを登録します。 次の例では、標準的な動詞登録を[!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].cs ファイル。  
  
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
  
## <a name="setting-the-default-verb"></a>既定の動詞を設定  
 既定の動詞は、ユーザーが Windows エクスプ ローラーでファイルをダブルクリックしたときに実行されるアクションです。 既定の動詞は、HKEY_CLASSES_ROOT の既定値として指定された動詞は\\*progid*\Shell キー。 既定の動詞は、HKEY_CLASSES_ROOT に指定された動詞は最初、値が指定されていない場合\\*progid*\Shell キーのリスト。  
  
> [!NOTE]
>  サイド バイ サイド配置で拡張機能の既定の動詞を変更する場合は、インストールと削除の影響を検討してください。 インストール中に元の既定値は上書きされます。  
  
## <a name="see-also"></a>関連項目  
 [side-by-side のファイルの関連付けを管理する](../extensibility/managing-side-by-side-file-associations.md)