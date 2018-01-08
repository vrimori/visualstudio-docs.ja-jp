---
title: "単一ファイル ジェネレーターを登録する |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- registration, custom tools
- custom tools, defining registry settings
ms.assetid: db7592c0-1273-4843-9617-6e2ddabb6ca8
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 22261c7485f1779eb3613c7ef5af693feeb51fbd
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="registering-single-file-generators"></a>単一ファイル ジェネレーターを登録します。
カスタム ツールで使用できるようにする[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]、ように登録する必要があります[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]をインスタンス化でき、特定のプロジェクトの種類に関連付けます。  
  
### <a name="to-register-a-custom-tool"></a>カスタム ツールを登録するには  
  
1.  カスタム ツールの DLL を登録するかで、[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ローカル レジストリかシステム レジストリの HKEY_CLASSES_ROOT 下です。  
  
     たとえば、ここでは、マネージ MSDataSetGenerator カスタム ツールに付属しているの登録情報[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\CLSID\{E76D53CC-3D4F-40A2-BD4D-4F3419755476}]  
    @="COM+ class: Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "InprocServer32"="C:\\WINDOWS\\system32\\mscoree.dll"  
    "ThreadingModel"="Both"  
    "Class"="Microsoft.VSDesigner.CodeGenerator.TypedDataSourceGenerator.DataSourceGeneratorWrapper"  
    "Assembly"="Microsoft.VSDesigner, Version=14.0.0.0, Culture=Neutral, PublicKeyToken=b03f5f7f11d50a3a"  
    ```  
  
2.  必要なレジストリ キーを作成[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]ジェネレーター ハイブ\\*GUID*場所*GUID* GUID は特定の言語のプロジェクト システムまたはサービスによって定義されます。 キーの名前では、カスタム ツールのプログラム上の名前になります。 カスタム ツールのキーには、次の値があります。  
  
    -   (既定)  
  
         任意。 カスタム ツールのわかりやすい説明を提供します。 このパラメーターは省略可、ただし推奨です。  
  
    -   CLSID  
  
         必須。 実装する COM コンポーネントのクラス ライブラリの識別子を指定<xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>です。  
  
    -   GeneratesDesignTimeSource  
  
         必須。 このカスタム ツールによって生成されたファイルから型をビジュアル デザイナーで使用可能な作成はかどうかを示します。 このパラメーターの値は、ビジュアル デザイナーで使用できない種類の 0 (ゼロ) またはビジュアル デザイナーで使用可能な型の (1) 1 である必要があります。  
  
    > [!NOTE]
    >  使用するカスタム ツールの対象となる言語ごとに個別にカスタム ツールを登録する必要があります。  
  
     たとえば、MSDataSetGenerator 登録自体 1 回言語ごとに。  
  
    ```  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{164b10b9-b200-11d0-8c61-00a0c91e29d5}\MSDataSetGenerator]  
    @="Microsoft VB Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
  
    [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\14.0\Generators\{fae04ec1-301f-11d3-bf4b-00c04f79efbc}\MSDataSetGenerator]  
    @="Microsoft C# Code Generator for XSD"  
    "CLSID"="{E76D53CC-3D4F-40a2-BD4D-4F3419755476}"  
    "GeneratesDesignTimeSource"=dword:00000001  
    ```  
  
## <a name="see-also"></a>参照  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator>   
 [単一ファイル ジェネレーターの実装](../../extensibility/internals/implementing-single-file-generators.md)   
 [ビジュアル デザイナーで型を公開します。](../../extensibility/internals/exposing-types-to-visual-designers.md)   
 [BuildManager オブジェクトの概要](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)