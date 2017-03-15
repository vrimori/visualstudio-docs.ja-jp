---
title: "ブランド化の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "[バージョン情報] ダイアログ ボックス"
  - "VSPackage、スプラッシュ スクリーン"
  - "VSPackage、ブランド化"
ms.assetid: a47b3645-574c-41c7-8a97-d071cd6b1e82
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# ブランド化の概要
スプラッシュ スクリーン ENT0ENT または \[出力\] ダイアログ ボックスで製品情報を表示するにはVSPackage次のいずれかで次の操作が必要です :  
  
-   公開 InstalledProducts のレジストリ キーの下に製品情報について説明しました。  
  
     または  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> を実装します  
  
 マネージ パッケージ フレームワークはInstalledProducts の \(MPF\) レジストリ キーの下にコントロールの登録に <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> の属性があります。  詳細については、「[方法: VSPackage をブランド化する \(C\# および Visual Basic\)](../misc/how-to-brand-a-vspackage-csharp-and-visual-basic.md)」を参照してください。  
  
 Visual Studio のライブラリは <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> の実装を作成するに `IVsInstalledProductImpl` テンプレート クラスを提供します。  詳細については、「[方法: VSPackage をブランド化する \(C\+\+\)](../misc/how-to-brand-a-vspackage-cpp.md)」を参照してください。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> を実行するには明示的に属性とテンプレートを使用してより強力です。  
  
-   \[入力\] ENT0ENT のアイコンとは異なるスプラッシュ スクリーンのアイコンを指定できます。  
  
-   **\*\*\* Help About \*\*\*** の製品名と異なるスプラッシュ スクリーンの製品名を指定できます。  
  
    > [!IMPORTANT]
    >  <xref:Microsoft.VisualStudio.Shell.InstalledProductRegistrationAttribute> を使用し<xref:Microsoft.VisualStudio.Shell.Interop.IVsInstalledProduct> を実装する場合はインターフェイスが優先されます。  
  
    > [!NOTE]
    >  同じアイコン リソースにスプラッシュ スクリーンと ENT3ENT \[出力\] ダイアログ ボックスに使用されます。  VSPackage のアイコン リソースにスプラッシュ スクリーンの 16 × 16 のイメージと ENT0ENT \[出力\] ダイアログ ボックスの 32 × 32 のイメージを含める必要があります。  1 種類のイメージ サイズだけを提供する場合は必要に応じてサイズが変更されその結果部分最適です。  
  
 関連するタスクの一覧については[Vspackages にあります。](../extensibility/internals/vspackages.md) を参照してください。  
  
## 参照  
 [Vspackages にあります。](../extensibility/internals/vspackages.md)   
 [Visual Studio ライブラリの概要](../misc/visual-studio-library-overview.md)