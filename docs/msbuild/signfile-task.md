---
title: SignFile タスク | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SignFile
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, SignFile task
- SignFile task [MSBuild]
ms.assetid: edef1819-ddeb-4e09-95de-fc7063ba9388
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6d063528b67712dd16136bfd3edec29643868517
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2018
ms.locfileid: "39154847"
---
# <a name="signfile-task"></a>SignFile タスク

指定された証明書を使用して、指定されたファイルに署名します。
  
## <a name="parameters"></a>パラメーター

 `SignFile` タスクのパラメーターの説明を次の表に示します。
  
 SHA-256 の証明書は .NET 4.5 以上が実行されているコンピューター上でのみ許可されることに注意してください。
  
> [!WARNING]
> Visual Studio 2013 Update 3 以降、このタスクには、ファイルのターゲット フレームワークのバージョンを指定できる新しい署名が用意されています。 ターゲット フレームワークが .NET 4.5 以上の場合のみ MSBuild プロセスで SHA-256 ハッシュが使用されるため、可能な限り新しい署名を使用することをお勧めします。 ターゲット フレームワークが .NET 4.0 以下である場合、SHA-256 ハッシュは使用されません。
  
|パラメーター|説明|
|---------------|-----------------|
|`CertificateThumbprint`|必須の `String` 型のパラメーターです。<br /><br /> 署名に使用する証明書を指定します。 この証明書は、現在のユーザーの個人ストアにある必要があります。|
|`SigningTarget`|必須の <xref:Microsoft.Build.Framework.ITaskItem> 型のパラメーターです。<br /><br /> 証明書で署名するファイルを指定します。|
|`TimestampUrl`|省略可能な `String` 型のパラメーターです。<br /><br /> タイム スタンプ サーバーの URL を指定します。|
|`TargetFrameworkVersion`|ターゲットに使用される .NET Framework のバージョンです。|
  
## <a name="remarks"></a>コメント

 上記のパラメーターに加えて、このタスクは <xref:Microsoft.Build.Utilities.Task> クラスからパラメーターを継承します。 これらの追加パラメーターのリストとその説明については、「[Task 基底クラス](../msbuild/task-base-class.md)」を参照してください。
  
## <a name="example"></a>例

 次に、`SignFile` タスクを使用して、`FilesToSign` アイテム コレクションで指定したファイルに、`Certificate` プロパティで指定された証明書で署名する例を示します。

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <FileToSign Include="File.exe" />
    </ItemGroup>
    <PropertyGroup>
        <Certificate>Cert.cer</Certificate>
    </PropertyGroup>
    <Target Name="Sign">
        <SignFile
            CertificateThumbprint="$(CertificateThumbprint)"
            SigningTarget="@(FileToSign)"
            TargetFrameworkVersion="v4.5" />
    </Target>
</Project>
```

> [!NOTE]
> 証明書の拇印は、証明書の SHA-1 ハッシュです。 詳細については、[信頼されたルート CA 証明書の SHA-1 ハッシュの取得](http://msdn.microsoft.com/en-us/dd641990-9a88-4228-a245-017797131a87)に関する記事を参照してください。
  
## <a name="see-also"></a>関連項目  
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)   
 [タスク](../msbuild/msbuild-tasks.md)