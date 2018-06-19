---
title: エディターでは、プロジェクトでファイルを開きますを決定する |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: d8fe054fa8e630b2f6c54cb78ef75b6c10ff74d3
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
ms.locfileid: "31130010"
---
# <a name="determining-which-editor-opens-a-file-in-a-project"></a>どのエディターが開き、プロジェクトのファイルを決定します。
プロジェクトで、ユーザーがファイルを開くと、最終的に、適切なエディターまたはそのファイルのデザイナーを開いて、ポーリング処理によって、環境が移動します。 環境内で採用されている最初の手順は、標準およびカスタムの両方のエディターに対して同じです。 ファイルを開くときに使用するエディターをポーリングするときに、環境でさまざまな条件を使用し、VSPackage は、このプロセス中に環境と連携する必要があります。  
  
 たとえば、ユーザーを選択すると、**開く**コマンドを**ファイル**] メニューの [を選択し、 `filename`.rtf (または .rtf 拡張子を持つ他のファイル) 環境の呼び出し、 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>最終的に繰り返し、ソリューション内のすべてのプロジェクト インスタンスを各プロジェクトの実装です。 プロジェクトには、優先順位によって、ドキュメントに対する要求を識別するフラグのセットが返されます。 最高の優先順位を使用して、環境が呼び出す、適切な<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>メソッドです。 ポーリング処理の詳細については[プロジェクトに追加してプロジェクト項目テンプレート](../../extensibility/internals/adding-project-and-project-item-templates.md)です。  
  
 その他のファイル プロジェクトでは、他のプロジェクトからの要求がないすべてのファイルを要求します。 これにより、標準のエディターで開く前に、カスタム エディターでドキュメントを開くことができます。 環境を呼び出す場合は、その他のファイル プロジェクト、ファイル、要求、<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>標準エディターでファイルを開くメソッドです。 環境では、いずれかの .rtf ファイルを処理する登録済みのエディターの内部リストを確認します。 この一覧は、次のキーのレジストリに格納されます。  
  
 [HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\\<`version`> \Editors\\{<`editor factory guid`>} \Extensions]  
  
 環境では、クラス識別子をサブキー DocObject を持つ任意のオブジェクトの hkey_classes_root \clsid キーにも確認します。 ファイルの拡張子がある場合がありますの埋め込みバージョンの Microsoft Word など、アプリケーションでは、Visual Studio では、インプレースが作成されます。 これらのドキュメント オブジェクトを実装する複合ファイルである必要があります、<xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>インターフェイス、またはオブジェクトを実装する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>インターフェイスです。  
  
 エディター ファクトリのレジストリで、.rtf ファイルがないかどうかは、環境で、HKEY_CLASSES_ROOT であるか\\.rtf キーと、エディターがあります指定が開きます。 HKEY_CLASSES_ROOT でファイルの拡張子が見つからない場合環境を使用して Visual Studio コアのテキスト エディター、テキスト ファイルである場合は、ファイルを開きます。  
  
 コアのテキスト エディターに失敗した場合、ファイルがテキスト ファイルでない場合、環境、バイナリ エディターのファイルを使用するに発生します。  
  
 環境が見つけられない場合、エディター .rtf 拡張機能のレジストリで、このエディター ファクトリを実装する VSPackage が読み込まれます。 環境の呼び出し、<xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>新しい VSPackage のメソッドです。 VSPackage の呼び出し`QueryService`の`SID_SVsRegistorEditor`を使用して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>環境とエディター ファクトリを登録するメソッド。  
  
 環境は、現在再チェック .rtf ファイルの新規登録エディター ファクトリの検索に登録されているエディターの内部リスト。 環境の実装を呼び出して、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>メソッド、ファイル名、ビューの種類を作成します。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat>   
 <xref:Microsoft.VisualStudio.OLE.Interop.IPersistStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.IsDocumentInProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3.OpenItem%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>