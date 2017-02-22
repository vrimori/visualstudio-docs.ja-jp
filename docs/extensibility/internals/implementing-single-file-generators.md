---
title: "単一ファイル ジェネレーターの実装 | Microsoft Docs"
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
  - "実装するカスタムのツール"
  - "プロジェクト [Visual Studio SDK] の機能拡張"
  - "プロジェクト [Visual Studio SDK] カスタム ツールの管理"
ms.assetid: fe9ef6b6-4690-4c2c-872c-301c980d17fe
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# 単一ファイル ジェネレーターの実装
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

カスタム ツール \(単一ファイル ジェネレーターと呼ばれる — [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] の [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] と  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] プロジェクト システムを拡張するために使用できます。  カスタム ツールは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> のインターフェイスを実装する COM コンポーネントです。  このインターフェイスを使用して単一の出力ファイルに一つの入力ファイルを変換します。  変換の結果はソース・コードまたは役に立つ他の出力がである場合があります。  カスタム ツールによって生成されたコード ファイルの 2 つがの例ではビジュアル デザイナーの変更に応じて生成されるサービス記述言語を使用して生成されたコードとファイルです \(WSDL\)。  
  
 カスタム ツールが読み込まれたり入力ファイルを保存するとプロジェクト システムは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> のメソッドはユーザーがツールに進行状況を報告できる<xref:Microsoft.VisualStudio.Shell.Interop.IVsGeneratorProgress> のコールバック インターフェイスへの参照を渡します。  
  
 カスタム ツールを生成する出力ファイルが入力ファイルの依存関係がプロジェクトに追加されます。  プロジェクト システムがカスタム ツールの <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> の実装によって返される文字列に基づいて自動的に出力ファイルの名前を決定します。  
  
 カスタム ツールは <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> のインターフェイスを実装する必要があります。  必要に応じて入力ファイルの外部ソースから情報を取得するために <xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite> のインターフェイスをサポートします。  いずれの場合もカスタム ツールを使用するにはシステムまたはの [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のローカルのレジストリに登録する必要があります。  カスタム ツールの登録の詳細については[単一ファイル ジェネレーターを登録します。](../../extensibility/internals/registering-single-file-generators.md) を参照してください。  
  
## 参照  
 [プロジェクトの既定の名前空間の決定](../../misc/determining-the-default-namespace-of-a-project.md)   
 [ビジュアル デザイナーで型を公開します。](../../extensibility/internals/exposing-types-to-visual-designers.md)