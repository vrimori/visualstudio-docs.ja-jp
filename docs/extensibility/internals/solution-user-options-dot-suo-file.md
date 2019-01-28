---
title: ソリューション ユーザー オプション (します。Suo) ファイル |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .suo files, VSPackages
- suo files, VSPackages
- solutions, .suo files
- solutions, user options
- solution user options (.suo) file
ms.assetid: 75258e0d-600d-4a3d-94f4-3d7ac12cb47c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bd77c125f6ac7b7efa8d0979658c7933dc1b9ec
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936993"
---
# <a name="solution-user-options-suo-file"></a>ソリューション ユーザー オプション (.Suo) ファイル
ソリューション ユーザー オプション (.suo) ファイルには、ユーザーごとにソリューションのオプションが含まれています。 このファイルは、ソース コード管理にないチェックする必要があります。  
  
 ソリューション ユーザー オプション (.suo) ファイルとは、構造化ストレージ、または複合、バイナリ形式で格納されているファイルです。 .Suo ファイル内の情報を識別するために使用されるキーをされているストリームの名前を持つには、ストリームにユーザー情報を保存します。 ソリューション ユーザー オプション ファイルは、ユーザーの設定を格納するために使用し、Visual Studio ソリューションを保存するときに自動的に作成されます。  
  
 環境では、.suo ファイルが開いたら、現在読み込まれているすべての Vspackage を列挙します。 VSPackage に実装されている場合、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>インターフェイス、その環境は、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.LoadUserOptions%2A> .suo ファイルからそのすべてのデータを読み込むことを VSPackage にメソッド。  
  
 .Suo ファイルに書き込まれた、VSPackage の責任にどのようなストリームを把握することをお勧めします。 それを記述した各ストリームでは、VSPackage にコールバックを通じて環境<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>ストリームの名前を指定すると、キーによって識別される特定のストリームを読み込めません。 ストリームの名前を渡してその特定のストリームの読み取りに VSPackage に、環境をバックアップし呼び出しますと`IStream`へのポインター、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.LoadPackageUserOpts%2A>メソッド。  
  
 別の呼び出しが行われた時点で、`LoadUserOptions`するかどうかは、読み取る必要があります .suo ファイルの別のセクションを参照してください。 このプロセスでは、すべて .suo ファイル内のデータ ストリームの読み取りし、環境によって処理されるまで続けられます。  
  
 ソリューションが保存または閉じると、環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionPersistence.SavePackageSolutionProps%2A>メソッドへのポインターを<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.SaveUserOptions%2A>メソッド。 `IStream`に渡されるを保存するバイナリ情報を含む、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts.WriteUserOptions%2A>メソッドを呼び出し、.suo ファイルに情報を書き込みます、 `SaveUserOptions` .suo に書き込む情報の別のストリームがあるかどうかをもう一度メソッドファイルです。  
  
 これら 2 つのメソッド、`SaveUserOptions`と`WriteUserOptions`へのポインターを渡して、.suo ファイルに保存する情報の各ストリームに対して再帰的に呼び出される`IVsSolutionPersistence`します。 .Suo ファイルに複数のストリームの書き込みを許可するには、再帰的に、呼び出されます。 この方法で、ユーザー情報は、ソリューションに保存されてし、次回にソリューションを開いたときにあることが保証されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistSolutionOpts>   
 [ソリューション](../../extensibility/internals/solutions.md)