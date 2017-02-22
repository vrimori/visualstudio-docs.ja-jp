---
title: "エディター ファクトリ | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "エディター [Visual Studio SDK] レガシー - エディター ファクトリ"
ms.assetid: cf4e8164-3546-441d-b465-e8a836ae7216
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# エディター ファクトリ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

エディターのファクトリはエディターのオブジェクトを作成し物理ビューと呼ばれるウィンドウ フレームに配置します。  これはエディターおよびデザイナーを作成するために必要なドキュメント データとドキュメントのビュー オブジェクトを作成します。  エディターのファクトリはVisual Studio コア エディターと標準エディターを作成する必要があります。  カスタム エディターはエディターのファクトリをオプションで作成できます。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> インターフェイスの実装によってエディターのファクトリを作成します。  次の例はエディターのファクトリを作成するに <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> を実装する方法を示しています :  
  
 [!code-vb[VSSDKEditorFactories#1](../extensibility/codesnippet/VisualBasic/editor-factories_1.vb)]
 [!code-cs[VSSDKEditorFactories#1](../extensibility/codesnippet/CSharp/editor-factories_1.cs)]  
  
 このエディターによって処理されるファイルの種類を開くエディターでは最初に読み込まれます。  特定のエディターまたは既定のエディターを開くことができます。  既定のエディターをクリックすると統合開発環境を \(IDE\) 開くための適切なエディターを確認しそれを開きます。  詳細については、「[どのエディターが開き、プロジェクト内のファイルを決定します。](../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)」を参照してください。  
  
## エディターのファクトリの登録  
 作成したエディターを使用するには最初に処理できるファイル拡張子がオブジェクトに関する情報を登録する必要があります。  
  
 VSPackage がマネージ コードで記述されている場合VSPackage の読み込み後エディターのファクトリを登録するにはマネージ パッケージ フレームワーク \(MPF\) のメソッド <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> を使用できます。  VSPackage がアンマネージ コードで記述されている場合<xref:Microsoft.VisualStudio.Shell.Interop.SVsRegisterEditors> サービスを使用してエディターのファクトリを登録する必要があります。  
  
### エディターのファクトリをマネージ コードを使用して登録します  
 VSPackage の `Initialize` のメソッドのエディターのファクトリを登録する必要があります。  最初の呼び出し `base.Initialize` は各エディターのファクトリの <xref:Microsoft.VisualStudio.Shell.Package.RegisterEditorFactory%2A> を呼び出します。  
  
 マネージ コードではVSPackage が自動的にこれを使用するとエディターのファクトリを登録解除する必要はありません。  または登録解除されるときのエディターのファクトリを <xref:System.IDisposable> を実行すると自動的に破棄されます。  
  
### エディターのファクトリをアンマネージ コードを使用して登録します  
 エディター パッケージの <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> の実装では`SVsRegisterEditors` を呼び出すために `QueryService` のメソッドを使用します。  これを行うには <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors> へのポインターを返します。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> のインターフェイスの実装を渡すことによって <xref:Microsoft.VisualStudio.Shell.Interop.IVsRegisterEditors.RegisterEditor%2A> のメソッドを呼び出します。  別のクラスの mplement <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> なります。  
  
## エディターのファクトリの登録処理  
 ここではVisual Studio がエディターのファクトリを使用するエディターを読み込むときに発生します :  
  
1.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] のプロジェクト システムの <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>。  
  
2.  このメソッドの戻り値エディターのファクトリ。  Visual Studio ではエディター パッケージの読み込みが遅延されますがプロジェクト システムが実際にエディターが必要です。  
  
3.  プロジェクト システムがエディターを必要とすると<xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>両方のドキュメントのビューおよびドキュメント データ オブジェクトを返す特殊なメソッドを呼び出します。  
  
4.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> エディターを使用してファクトリに Visual Studio によって呼び出しがドキュメント データ オブジェクトとドキュメントのビュー オブジェクトの両方を返す場合Visual Studio はドキュメント ウィンドウを作成しドキュメント ビュー オブジェクトを配置してドキュメント データ オブジェクトの連続したドキュメントのテーブル \(RDT\) にエントリを作成します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>   
 [実行中のドキュメント テーブル](../extensibility/internals/running-document-table.md)