---
title: 単一ファイル ジェネレーターの登録 |Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e601b3fcf8bd702c1bc6cde427766d0f107e6bd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780985"
---
# <a name="registering-single-file-generators"></a>単一ファイル ジェネレーターの登録
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

カスタム ツールで使用できるようにする[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]、そのために登録する必要があります[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]をインスタンス化でき、特定のプロジェクトの種類に関連付けます。  
  
### <a name="to-register-a-custom-tool"></a>カスタム ツールを登録するには  
  
1.  カスタム ツールの DLL を登録するかで、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ローカル レジストリかシステム レジストリの HKEY_CLASSES_ROOT の下。  
  
     たとえば、マネージ MSDataSetGenerator カスタム ツールに付属している登録情報をここでは[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  必要なレジストリ キーを作成[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]ジェネレーターでの hive\\*GUID*場所*GUID* GUID は、特定の言語のプロジェクト システムまたはサービスによって定義されます。 カスタム ツールのプログラムによる名前のキーの名前になります。 カスタム ツールのキーでは、次の値があります。  
  
    -   (既定)  
  
         任意。 カスタム ツールのわかりやすい説明を提供します。 このパラメーターは省略可、ただし推奨されるは。  
  
    -   CLSID  
  
         必須。 実装する COM コンポーネントのクラス ライブラリの識別子を指定します<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>します。  
  
    -   GeneratesDesignTimeSource  
  
         必須。 このカスタムのツールによって生成されたファイルからの種類をビジュアル デザイナーを使用できる構成されるかどうかを示します。 このパラメーターの値は、ビジュアル デザイナーを使用できない種類の 0 (ゼロ) やビジュアル デザイナーを使用可能な型の (1 つ) の 1 にする必要があります。  
  
    > [!NOTE]
    >  使用するカスタム ツールの対象となる言語ごとに個別にカスタム ツールを登録する必要があります。  
  
     たとえば、MSDataSetGenerator 自身を登録 1 回の各言語。  
  
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
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)   
 [プロジェクトの既定の Namespace を決定します。](../../misc/determining-the-default-namespace-of-a-project.md)   
 [ビジュアル デザイナーへの型を公開します。](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager オブジェクトの概要](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)

