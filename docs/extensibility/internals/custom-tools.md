---
title: "カスタム ツール | Microsoft Docs"
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
  - "Vspackages にある、カスタム ツール"
  - "カスタム ツール [Visual Studio]"
  - "カスタム ツール"
ms.assetid: d669f154-9b23-48b6-b9f6-7419c8dd61a6
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# カスタム ツール
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

ツールを使用してファイルを保存するたびに  *カスタム ツールは* プロジェクトを実行し項目とツールを関連付けることができます。  場合によっては *単一ファイル ジェネレーター*  と呼ばれる特定のカスタム ツールがデータのコードをその逆も生成される変換を実行するために使用されます。  たとえば単一ファイル ジェネレーターは.settings ファイルおよび .resx ファイルから [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] と  [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] のソース・コードを作成します。  生成されたソース・コードを .settings ファイルおよび .resx ファイルのデータへの厳密に型指定されたアクセスを提供します。  [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] と  [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] の種類のプロジェクトではカスタム ツールをサポートします ; [!INCLUDE[vcprvc](../../debugger/includes/vcprvc_md.md)] のプロジェクトは。  独自のプロジェクトの種類はカスタム ツールをサポートできます。  
  
 カスタム ツールは `IVsSingleFileGenerator` のインターフェイスを実装して登録されたコンポーネントです。  
  
 カスタム ツールは `ProjectItem` のインターフェイス オブジェクトに関連付けられエディターやデザイナーなどです。  カスタム ツールは入力として `ProjectItem` によって表されるファイルを受け取りファイル名が `DefaultExtension` のメソッドによる新しいファイルを作成します。  
  
## このセクションの内容  
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> のインターフェイスをカスタム ツールを実行する方法について説明します。  
  
 [プロジェクトの既定の名前空間の決定](../../misc/determining-the-default-namespace-of-a-project.md)  
 使用する言語に基づいて適切な名前空間を確認する方法を説明します。  
  
 [単一ファイル ジェネレーターを登録します。](../../extensibility/internals/registering-single-file-generators.md)  
 カスタム ツールのすべてのレジストリ エントリについて説明します。  
  
 [ビジュアル デザイナーで型を公開します。](../../extensibility/internals/exposing-types-to-visual-designers.md)  
 プロジェクト システムが一時的なポータブル実行可能ファイルによってアクセスによって生成されるクラスと型にビジュアル デザイナーのサポートを提供する \(PE\) 方法について説明します。  
  
 [プロジェクト項目のプロパティを永続化します。](../../extensibility/persisting-the-property-of-a-project-item.md)  
 プロジェクト ファイルでソース ファイルを作成するなど永続化する方法を示します。プロジェクト項目のプロパティ  
  
## 関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator> に関する詳細を提供しプロジェクトにコンパイルまたは追加できる単一の出力ファイルに一つの入力ファイルを変換する。  
  
 <xref:EnvDTE.ProjectItem>  
 プロジェクト項目を表す `ProjectItem` のインターフェイスを示しています。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A>  
 出力ファイル名を指定したファイル名拡張子を取得します `DefaultExtension` の方法の詳細を説明します。  
  
## 関連項目  
 [プロジェクトの拡張](../../extensibility/extending-projects.md)  
 コード ファイルおよびリソース ファイルを管理する [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] のプロジェクトとソリューションをソース管理を使用してを実装する方法について説明します。