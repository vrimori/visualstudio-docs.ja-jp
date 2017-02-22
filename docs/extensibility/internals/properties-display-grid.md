---
title: "プロパティ グリッドの表示] | Microsoft Docs"
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
  - "プロパティ [Visual Studio SDK] グリッド"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# プロパティ グリッドの表示]
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

グリッド内の ENT0ENT \[出力\] ウィンドウに表示します。  左の列にはプロパティ名が含まれています ; 右側の列にはプロパティ値を含みます。  
  
## グリッドを使用  
 2 列のリストはデザイン時と現在の設定で変更できる構成に依存しないプロパティを示します。  すべてのプロパティが表示されないことに注意してください。  プロパティは<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> メソッドの実装で隠れるように設定できます。  具体的には子プロパティを参照するプロパティを非表示にするには [子プロパティを持つ非表示のプロパティ](../../misc/hiding-properties-that-have-child-properties.md)。  
  
 \[入力\] ENT0ENT ウィンドウの情報を押しながらは<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> を使用します。  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> は ENT4ENT \[出力\] ウィンドウに表示する関連プロパティを持つ選択できるオブジェクトを含む各ペインの VSPackages によって呼び出されます。  ソリューション エクスプローラーで <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> の実装はプロジェクト階層で <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> を使用して階層の browseable オブジェクトを取得するに `GetProperty` を呼び出します。  
  
 VSPackage が <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> をサポートする階層の項目を指定する <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> の値を使用して <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> を使用しようとします。  
  
 \(IDE\) を実装する  **ソリューション エクスプローラー**  指定されたウィンドウのパッケージがどこから <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> を構成するときは <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackage プロジェクトを作成する必要はありません。  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> はIDE で呼び出す 3 とおりの方法で構成されます :  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> は ENT3ENT \[入力\] ウィンドウで表示するように選択されたオブジェクトの数。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> は\[出力\] ウィンドウに表示 ENT0ENT のために選択した `IDispatch` のオブジェクトを返します。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> はユーザーが選択した <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> によって返されるオブジェクトができるようにします。  これはVSPackage を視覚的に UI ユーザーが選択を更新できるようにします。  
  
 `IDispatch` から抽出 ENT1ENT \[出力\] ウィンドウに情報は参照されるプロパティを取得します。  プロパティ ブラウザーはプロパティを `IDispatch::GetTypeInfo` から派生したクエリ `ITypeInfo` でサポートするオブジェクトに `IDispatch` を確認するにはを使用します。  ブラウザーは\[出力\] ウィンドウ ENT0ENT 設定しグリッドに表示される個々のプロパティの値を変更するにはこれらの値を使用します。  プロパティの情報はオブジェクト自体で保持されます。  
  
 返されたオブジェクトは `IDispatch` をサポートするため呼び出し元は必要な情報を表す定義済みのディスパッチ識別子 \(DISPID\) の `IDispatch::Invoke` または `ITypeInfo::Invoke` を呼び出してオブジェクト名などの情報を取得できます。  宣言された DISPIDs はユーザー定義の識別子によって競合しないようにになります。  
  
 選択したオブジェクトの特定のプロパティ属性を使用してフィールドの ENT0ENT \[出力\] ウィンドウに表示の種類。  これらのフィールドはカスタム エディター ダイアログ ボックスにエディット ボックスドロップダウン リストおよびのリンクを示します。  
  
-   列挙リストに含まれる値は`IDispatch` への <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> のクエリで取得します。  列挙リストから取得した値をプロパティ グリッドで各フィールド名をクリックするか値をクリックしてドロップダウン リストから新しい値を選択することによって変更できます。  列挙リストから定義済みの設定を持つプロパティではプロパティの一覧サイクルの名前を選択できる項目でダブルをクリックします。  2 種類の選択をの定義済みのプロパティではtrue\/false などの選択に切り替えるには各プロパティ名をクリックします。  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> が `false` 場合は値が変更されたことを示し値は太字で表示されます。  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> の値が元の値にリセットできるかどうかを確認するために使用されます。  その場合既定で値を右クリックすると表示  **リセット**  メニューのを選択することによって返されることがあります。  それ以外の場合は既定値に手動で返す必要があります。  または <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ではデザイン時に表示するプロパティの名前をローカライズを非表示にすると実行時に表示されるプロパティ名には影響しません。  
  
-   省略記号ボタン \(...\) をクリックするとユーザーが選択できるプロパティ値の一覧 \(カラーピッカーやフォントの一覧など\)。  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> はこれらの値を指定します。  
  
## 参照  
 [プロパティを拡張します。](../../extensibility/internals/extending-properties.md)