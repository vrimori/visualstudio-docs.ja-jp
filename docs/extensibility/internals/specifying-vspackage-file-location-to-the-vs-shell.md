---
title: "VS Shell VSPackage ファイルの場所を指定します。 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マネージ vspackages にある、ファイルの場所"
  - "Vspackages にある、パッケージ ファイルの場所を管理します。"
ms.assetid: beb8607a-4183-4ed2-9ac8-7527f11513b1
caps.latest.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 20
---
# VS Shell VSPackage ファイルの場所を指定します。
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] アセンブリを VSPackage を読み込む DLL を検索できる必要があります。 次の表に示すとおり、さまざまな方法でそれを検索できます。  
  
|メソッド|説明|  
|----------|--------|  
|コードベースのレジストリ キーを使用します。|コードベース キーは、ダイレクトを使用できます [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] に任意のファイルの絶対パスから VSPackage アセンブリを読み込みます。 キーの値には、DLL にファイル パスを指定する必要があります。 これが最善の方法は、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] パッケージ アセンブリを読み込みます。 この手法は、「コードベースと秘密のインストール ディレクトリ手法です」と呼ばれることがあります。 登録時に、コードベースの値は登録属性クラスのインスタンスを通じて、 <xref:Microsoft.VisualStudio.Shell.RegistrationAttribute.RegistrationContext> 型です。|  
|DLL を置く、 **PrivateAssemblies** ディレクトリ。|内のアセンブリを配置、 **PrivateAssemblies** のサブディレクトリ、 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ディレクトリ。 アセンブリに配置 **PrivateAssemblies** は自動的に検出されるに表示されない、 **参照の追加** \] ダイアログ ボックス。 違い **PrivateAssemblies** と **PublicAssemblies** はアセンブリで **PublicAssemblies** に列挙されて、 **参照の追加** \] ダイアログ ボックス。 "コードベースと秘密 installation directory"手法を使用しないように選択したかどうかは、インストールする必要があります、 **PrivateAssemblies** ディレクトリ。|  
|厳密な名前のアセンブリとアセンブリのレジストリ キーを使用します。|アセンブリ キーは、明示的に指示するために使用できます [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] を読み込む、厳密な名前の VSPackage アセンブリ。 キーの値は、アセンブリの厳密な名前にする必要があります。|  
|DLL を置く、 **PublicAssemblies** ディレクトリ。|最後に、アセンブリに配置できるもの **PublicAssemblies** サブディレクトリ。 アセンブリに配置 **PublicAssemblies** が自動的に検出されにも表示されます、 **参照の追加** \] ダイアログ ボックスで [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]します。<br /><br /> 格納のみ VSPackage アセンブリ、 **PublicAssemblies** ディレクトリに含まれている場合に、VSPackage 他の開発者が再利用するのには、コンポーネントが管理されています。 アセンブリの大部分は、この条件を満たしていません。|  
  
> [!NOTE]
>  すべての依存アセンブリの厳密な名前の署名付きのアセンブリを使用します。 これらのアセンブリは、独自のディレクトリまたはグローバル アセンブリ キャッシュ \(GAC\) にもインストールする必要があります。 これは弱い名前のバインドと呼ばれる、同じ基本ファイル名を持つアセンブリとの競合を防止できます。