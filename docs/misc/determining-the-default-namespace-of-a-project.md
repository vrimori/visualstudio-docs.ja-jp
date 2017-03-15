---
title: "プロジェクトの既定の名前空間の決定 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "カスタムツール、既定の名前空間の計算"
ms.assetid: 6d890676-7016-458c-8a6a-95cc0a068612
caps.latest.revision: 13
caps.handback.revision: 13
manager: "douge"
---
# プロジェクトの既定の名前空間の決定
`CustomToolNamespace` の [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]値に `CustomToolNamespace` 入力ファイルのプロパティがに設定されて <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> のメソッドに渡される既定の名前空間のパラメーターの値になります。  それ以外 `Generate` に渡される `wszDefaultNamespace` のパラメーターはルート名前空間と常に等しくなります。  名前空間の詳細については[名前空間キーワード](/dotnet/csharp/language-reference/keywords/namespace-keywords) を参照してください。  
  
 [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] のフォルダー ベースの名前空間。  つまり名前空間はカスタム ツールを含むフォルダーの名前とルート名前空間から構成されます。  各フォルダー名が有効な識別子に変換されピリオドすべての名前を区切ります。  たとえば入力ファイルが FolderC \\ FolderA \\ FolderB \\ MyInput.txt 場合ルート名前空間 CL9 は計算された既定の名前空間が **CL9.FolderA.FolderB.FolderC** です。  
  
 この規則の例外は階層のチェーンが Web 参照のフォルダーが含まれる場合に発生します。  たとえば、次のような場合を想定してみます。  
  
-   FolderC はWeb 参照\] フォルダー名前空間です **CL9.FolderC** いません。  
  
-   FolderB はWeb 参照\] フォルダー名前空間です **CL9.FolderB.FolderC** いません。  
  
 つまり名前空間には次の形式を使用して :  
  
```  
rootNamespace.webReferenceFolder.containedFolder.containedFolder ...  
```  
  
## 参照  
 [単一ファイル ジェネレーターの実装](../extensibility/internals/implementing-single-file-generators.md)   
 [単一ファイル ジェネレーターを登録します。](../extensibility/internals/registering-single-file-generators.md)   
 [ビジュアル デザイナーで型を公開します。](../extensibility/internals/exposing-types-to-visual-designers.md)