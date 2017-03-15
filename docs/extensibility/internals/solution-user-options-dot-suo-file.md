---
title: "ソリューション ユーザー オプション (します。Suo) ファイル | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - ".suo ファイル、vspackages にあります。"
  - "suo ファイル、vspackages にあります。"
  - "ソリューション、.suo ファイル"
  - "ソリューション ユーザー オプション"
  - "ソリューション ユーザー オプション (.suo) ファイル"
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# ソリューション ユーザー オプション (します。Suo) ファイル
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ソリューション ユーザー オプション \(.suo\) ファイルには、ユーザーごとにソリューションのオプションが含まれています。 ソース コード管理、このファイルをチェックしない必要があります。  
  
 ソリューション ユーザー オプション \(.suo\) ファイルとは、構造化ストレージ、または複合、バイナリ形式で格納されているファイルです。 .Suo ファイル内の情報を識別するために使用されるキー、ストリームの名前には、ストリームにユーザー情報を保存します。 ソリューション ユーザー オプション ファイルは、ユーザー設定の格納に使用され、Visual Studio ソリューションを保存するときに自動的に作成されます。  
  
 環境では、.suo ファイルが開いたら、現在読み込まれているすべての VSPackages を列挙します。 VSPackage を実装する場合、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts> インターフェイスでは、環境呼び出します、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> .suo ファイルからそのすべてのデータを読み込むことを要求した VSPackage のメソッドです。  
  
 VSPackage の責任にどのようなストリームのトピックを .suo ファイルに書き込まれたことをお勧めします。 これを作成した各ストリームの VSPackage にコールバックを通じて環境 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> 、ストリームの名前が指定されたキーによって識別される特定のストリームの読み込みにします。 環境を呼び出して、ストリームの名前を渡してその特定のストリームの読み取りに VSPackage と `IStream` へのポインター、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A> メソッドです。  
  
 別の呼び出しが行われた時点で、 `LoadUserOptions` するかどうかは、読み取る必要のある .suo ファイルの別のセクションを参照してください。 .Suo ファイル内のデータ ストリームのすべてを読み取るし、環境によって処理されるまで、この処理が続きます。  
  
 ソリューションが保存または閉じると、環境の呼び出しと、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A> メソッドへのポインターを <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A> メソッドです。`IStream` に渡されるを保存するバイナリ情報を含む、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A> メソッドを呼び出し、.suo ファイルに情報を書き込みます、 `SaveUserOptions` メソッドを再び .suo ファイルに書き込む情報の別のストリームがあるかどうか。  
  
 これら 2 つの方法では、 `SaveUserOptions` と `WriteUserOptions`, へのポインターを渡して、.suo ファイルに保存する情報の各ストリームに対して再帰的に呼び出される `IVsSolutionPersistence`です。 .Suo ファイルに複数のストリームの書き込みを許可するには、再帰的に、呼び出されます。 このようにでは、ユーザー情報は、ソリューションは、永続化し、次回にソリューションを開いたときになることが保証します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [ソリューション](../../extensibility/internals/solutions.md)