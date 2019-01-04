---
title: エディターがプロジェクトでファイルを開きますの決定 |Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], determining which editor opens a file
- projects [Visual Studio SDK], determining which editor opens file
- project types, determining which editor opens a file
- persistence, determining which editor opens a file
ms.assetid: acbcf4d8-a53a-4727-9043-696a47369479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b61aa726a7088d08db6d759a9835816dcaf826a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941061"
---
# <a name="determine-which-editor-opens-a-file-in-a-project"></a>特定のエディターがプロジェクトでファイルを開きます
プロジェクトでユーザーがファイルを開くと、最終的に、適切なエディターまたはデザイナーがそのファイルを開いて、ポーリング処理によって、環境が移動します。 環境で採用されている最初の手順では、標準とカスタムの両方のエディターに同じです。 環境ではファイルを開くときに使用するエディターをポーリングするときに、さまざまな条件を使用し、VSPackage は、このプロセス中に、環境と調整する必要があります。  
  
 たとえば、ユーザーが選択すると、**オープン**コマンドを**ファイル**] メニューの [を選択し、 *filename.rtf* (またはその他の任意のファイルを *.rtf*拡張機能)、環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>最終的に、ソリューション内のすべてのプロジェクト インスタンスを繰り返し、プロジェクトごとに実装します。 プロジェクトでは、優先順位によって、ドキュメントに対する要求を識別するフラグのセットを返します。 最高の優先順位を使用して、環境が呼び出す、適切な<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッド。 ポーリングのプロセスの詳細については、次を参照してください。[プロジェクトとプロジェクト項目テンプレートを追加](../../extensibility/internals/adding-project-and-project-item-templates.md)します。  
  
 その他のファイル プロジェクトでは、他のプロジェクトでは請求されないすべてのファイルを要求します。 これにより、標準のエディターで開く前に、カスタム エディターでドキュメントを開くことができます。 環境を呼び出す場合、その他のファイル プロジェクトには、ファイルが要求を<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>メソッドを標準のエディターでファイルを開きます。 環境を処理する 1 つの登録済みのエディターの内部リストを確認します。 *.rtf*ファイル。 この一覧は、レジストリ内で、次のキーにあります。  
  
 **Hkey_local_machine \software\microsoft\visualstudio\\\<バージョン > \Editors\\\<エディター ファクトリの guid > \Extensions**
  
 環境クラス id も確認します、 **hkey_classes_root \clsid**サブキーがあるすべてのオブジェクトのキー **DocObject**します。 ファイル拡張子は、そこで見つかった場合埋め込みバージョンの Microsoft Word など、アプリケーションが Visual Studio で、インプレースを作成します。 これらのドキュメント オブジェクトを実装する複合ファイルである必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>インターフェイス、またはオブジェクトを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイス。  
  
 エディター ファクトリがない場合は *.rtf*環境を検索し、レジストリで、ファイル、 **HKEY_CLASSES_ROOT\\.rtf**キーし、があります指定されたエディターが開きます。 ファイル拡張子が見つからない場合**HKEY_CLASSES_ROOT**環境を使用して、Visual Studio のコアのテキスト エディター ファイルを開いて、テキスト ファイルの場合は。  
  
 テキストのコア エディターが失敗した場合、ファイルがテキスト ファイルでない場合、環境、バイナリ エディターのファイルを使用するに発生します。  
  
 環境でのエディターが検出した場合、 *.rtf*そのレジストリの拡張機能は、このエディターのファクトリを実装する VSPackage を読み込みます。 環境は、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>新しい VSPackage のメソッド。 VSPackage 呼び出し`QueryService`の`SID_SVsRegistorEditor`を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>環境とエディターのファクトリを登録するメソッド。  
  
 環境では、新しく登録されたエディター ファクトリの検索に登録されているエディターの内部リストを再 *.rtf*ファイル。 環境の実装を呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッドを作成するファイル名とビューの種類。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>