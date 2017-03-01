---
title: "単一ファイル ジェネレーターを登録する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 239f68b8bdbaf910f25b9fbe6e0fdd7061fe0f16
ms.lasthandoff: 02/22/2017

---
# <a name="registering-single-file-generators"></a>単一ファイル ジェネレーターを登録します。
カスタム ツールで利用できるように[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、そのために登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]をインスタンス化でき、特定のプロジェクトの種類に関連付けます。  
  
### <a name="to-register-a-custom-tool"></a>カスタム ツールを登録するには  
  
1.  カスタム ツールの DLL を登録するかで、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ローカル レジストリまたはシステム レジストリの HKEY_CLASSES_ROOT の下にします。  
  
     たとえば、ここではマネージ MSDataSetGenerator カスタム ツールに付属している登録情報[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  必要なレジストリ キーを作成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ジェネレーターの下の hive\\*GUID* 、 *GUID* GUID は、特定の言語のプロジェクト システムまたはサービスによって定義されます。 キーの名前は、カスタム ツールのプログラムの名前になります。 カスタム ツールのキーには、次の値があります。  
  
    -   (既定)  
  
         省略可能です。 カスタム ツールのわかりやすい説明を提供します。 このパラメーターは省略可、ただし推奨です。  
  
    -   CLSID  
  
         必須です。 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>。</xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>を実装する COM コンポーネントのクラス ライブラリの識別子を指定します。  
  
    -   GeneratesDesignTimeSource  
  
         必須です。 ビジュアル デザイナーでこのカスタムのツールによって生成されたファイルからの型を使用可能なことにはかどうかを示します。 このパラメーターの値は、ビジュアル デザイナーを使用できない種類の 0 (ゼロ) やビジュアル デザイナーで使用可能な型の場合 (1 つ) は 1 にする必要があります。  
  
    > [!NOTE]
    >  使用可能なカスタム ツールの対象となる言語ごとに個別にカスタム ツールを登録する必要があります。  
  
     たとえば、MSDataSetGenerator 自らを登録一度言語ごとに。  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{e6fdf8b0-f3d1-11d4-8576-0002a516ece8}\MSDataSetGenerator]  
    @="Microsoft J# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator></xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)   
 [プロジェクトの既定の Namespace を決定します。](../../misc/determining-the-default-namespace-of-a-project.md)   
 [ビジュアル デザイナーで型を公開します。](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager オブジェクトの概要](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
