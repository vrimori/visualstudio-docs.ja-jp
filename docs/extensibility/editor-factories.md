---
title: エディター ファクトリ |Microsoft ドキュメント
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - editor factories
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 676918b6366837b6ee77cf27bd5fba9fbf608729
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="editor-factories"></a>エディター ファクトリ
エディター ファクトリは、エディターのオブジェクトを作成し、物理ビューと呼ばれる、ウィンドウ フレームに格納します。 これは、ドキュメント データおよびエディターおよびデザイナーを作成するために必要なドキュメント ビュー オブジェクトを作成します。 Visual Studio コア エディターと任意の標準エディターを作成するには、エディター ファクトリが必要です。 カスタム エディターは、エディター ファクトリのオプションで作成できます。  
  
 エディター ファクトリを実装することで作成する、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイスです。 次の例は、実装する方法を示します<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>エディター ファクトリを作成します。  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-csharp[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 エディターは、そのエディターによって処理されるファイルの種類を開く初めて読み込まれます。 特定のエディター、または既定のエディターを開くことができます。 既定のエディターを選択した場合、統合開発環境 (IDE) を開くには正しいエディターを決定しを開きます。 詳細については、次を参照してください。[プロジェクトでファイルを開くエディターを決定する](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)です。  
  
## <a name="registering-editor-factories"></a>エディター ファクトリの登録  
 作成したエディターを使用することができます、前に、に関する情報を処理できるファイル拡張子を含む最初に登録する必要があります。  
  
 Managed Package Framework (MPF) メソッドを使用することができる場合は、VSPackage は、マネージ コードで記述された、 <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> VSPackage が読み込まれた後に、エディター ファクトリを登録します。 VSPackage が、アンマネージ コードで記述されたかどうかを使用して、エディター ファクトリを登録する必要があります、<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors>サービス。  
  
### <a name="registering-an-editor-factory-by-using-managed-code"></a>マネージ コードを使用して、エディター ファクトリを登録します。  
 VSPackage ので、エディター ファクトリを登録する必要があります、`Initialize`メソッドです。 まず`base.Initialize`、まず<xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A>エディター ファクトリごとの  
  
 マネージ コードではありません、エディター ファクトリの登録を解除する必要があります、VSPackage がこれを処理するため。 また、エディター ファクトリを実装する場合<xref:System.IDisposable>、登録が解除時に自動的に破棄します。  
  
### <a name="registering-an-editor-factory-by-using-unmanaged-code"></a>アンマネージ コードを使用して、エディター ファクトリを登録します。  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>エディター パッケージを使用するための実装、`QueryService`メソッドを呼び出す`SVsRegisterEditors`です。 ポインターを返しますこれ<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors>です。 呼び出す、<xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A>メソッドの実装を渡すことによって、<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>インターフェイスです。 Mplement する必要があります<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>が別のクラスです。  
  
## <a name="the-editor-factory-registration-process"></a>エディター ファクトリの登録プロセス  
 次のプロセスは、Visual Studio は、エディター ファクトリを使用して、エディターを読み込むときに発生します。  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]システム コールをプロジェクト<xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>です。  
  
2.  このメソッドは、エディター ファクトリを返します。 Visual Studio 遅延は、プロジェクト システムは、エディターを実際に必要になるまで、ただし、エディターのパッケージを読み込みます。  
  
3.  Visual Studio プロジェクト システムに、エディターが必要がある場合は呼び出して<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>、特殊なメソッドをドキュメントの表示と、ドキュメントの両方のデータ オブジェクトを返します。  
  
4.  場合にエディター ファクトリを使用して、Visual Studio によって呼び出す<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>ドキュメント データ オブジェクトとドキュメント ビュー オブジェクトの両方を返す、Visual Studio ドキュメント ウィンドウを作成、ドキュメント ビュー オブジェクトを配置し、実行中の文書に入力ドキュメント データ オブジェクトのテーブル (RDT)。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [ドキュメント テーブルの実行](../extensibility/internals/running-document-table.md)