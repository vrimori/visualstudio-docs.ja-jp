---
title: "ソリューション ユーザー オプション (です。Suo) ファイル |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a71f3e14c6a8c87290de2a6204fa28f99a8cabe8
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="solution-user-options-suo-file"></a>ソリューション ユーザー オプション (です。Suo) ファイル
ソリューション ユーザー オプション (.suo) ファイルには、ユーザーごとにソリューションのオプションが含まれています。 このファイルは、ソース コード管理いないチェックする必要があります。  
  
 ソリューション ユーザー オプション (.suo) ファイルとは、構造化ストレージ、または複合、バイナリ形式で格納されているファイルです。 ストリームにユーザー情報を保存するには、ストリームの .suo ファイル内の情報の識別に使用されるキーの名前に置き換えます。 ソリューション ユーザー オプション ファイルは、ユーザー設定の格納に使用し、Visual Studio ソリューションを保存するときに自動的に作成されます。  
  
 環境が .suo ファイルを開くときに現在読み込まれているすべての VSPackages を列挙します。 VSPackage に実装されている場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>インターフェイス、その環境の呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> .suo ファイルからすべてのデータを読み込むことを確認する VSPackage のメソッドです。  
  
 ストリーム新機能を把握する VSPackage の責任に .suo ファイルに書き込まれたことをお勧めします。 書き込んだ各ストリームに対して VSPackage にコールバックを介して環境<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>ストリームの名前を指定すると、キーによって識別される特定のストリームを読み込めません。 環境を呼び出して、ストリームの名前を渡してその特定のストリームの読み取りに VSPackage と`IStream`へのポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>メソッドです。  
  
 別の呼び出しが行われた時点で、`LoadUserOptions`の .suo ファイルを読み取る必要のある別のセクションがないかどうかにします。 このプロセスは、すべて .suo ファイル内のデータ ストリームの読み取りし、環境によって処理されるまで続きます。  
  
 ソリューションが保存するか閉じる、環境の呼び出し時、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>メソッドへのポインターを<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>メソッドです。 `IStream`に渡されるを保存するバイナリ情報を含む、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>メソッドを呼び出し、.suo ファイルに情報を書き込みます、 `SaveUserOptions` .suo に情報に書き込むの別のストリームがないかどうかをもう一度メソッドファイルです。  
  
 これら 2 つの方法では、`SaveUserOptions`と`WriteUserOptions`へのポインターを渡して、.suo ファイルに保存する情報の各ストリームに対して再帰的に呼び出される`IVsSolutionPersistence`です。 .Suo ファイルに複数のストリームの書き込みを許可するには、再帰的に、呼び出されます。 その方法でユーザー情報は、ソリューションに保存されてし、に存在する、次回ソリューションを開くことが保証します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [ソリューション](../../extensibility/internals/solutions.md)