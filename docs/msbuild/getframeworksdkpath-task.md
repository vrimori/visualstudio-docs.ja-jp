---
title: GetFrameworkSdkPath タスク | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GetFrameworkSdkPath
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- GetFrameworkSdkPath task [MSBuild]
- MSBuild, GetFrameworkSdkPath task
ms.assetid: 2ef82b98-02b6-40cf-a9b5-f0e882fb5064
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fb1ca2a4c77471f4b6767269e511d690c6c094a1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947271"
---
# <a name="getframeworksdkpath-task"></a>GetFrameworkSdkPath タスク
[!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] へのパスを取得します。  
  
## <a name="task-parameters"></a>タスク パラメーター  
 `GetFrameworkSdkPath` タスクのパラメーターの説明を次の表に示します。  
  
|パラメーター|説明|  
|---------------|-----------------|  
|`FrameworkSdkVersion20Path`|省略可能な `String` 型の読み取り専用の出力パラメーターです。<br /><br /> 存在する場合、.NET SDK バージョン 2.0 のパスを返します。 それ以外の場合は、`String.Empty` を返します。|  
|`FrameworkSdkVersion35Path`|省略可能な `String` 型の読み取り専用の出力パラメーターです。<br /><br /> 存在する場合、.NET SDK バージョン 3.5 のパスを返します。 それ以外の場合は、`String.Empty` を返します。|  
|`FrameworkSdkVersion40Path`|省略可能な `String` 型の読み取り専用の出力パラメーターです。<br /><br /> 存在する場合、.NET SDK バージョン 4.0 のパスを返します。 それ以外の場合は、`String.Empty` を返します。|  
|`Path`|省略可能な `String` 型の出力パラメーターです。<br /><br /> 何らかのバージョンが存在する場合、最新の .NET SDK のパスが含まれます。 それ以外の場合は、`String.Empty` を返します。|  
  
## <a name="remarks"></a>コメント  
 上記のパラメーター以外に、このタスクは <xref:Microsoft.Build.Tasks.TaskExtension> クラスからパラメーターを継承します。このクラス自体は、<xref:Microsoft.Build.Utilities.Task> クラスから継承されます。 これらの追加のパラメーターの一覧とその説明については、「[TaskExtension Base Class](../msbuild/taskextension-base-class.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例では、`GetFrameworkSdkPath` タスクを使用し、[!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] のパスを `SdkPath` プロパティに保存します。  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Target Name="GetPath">  
        <GetFrameworkSdkPath>  
            <Output  
                TaskParameter="Path"  
                PropertyName="SdkPath" />  
        </GetFrameworkSdkPath>  
        <Message Text="$(SdkPath)"/>  
    </Target>  
</Project>  
```  
  
## <a name="see-also"></a>関連項目  
 [タスク](../msbuild/msbuild-tasks.md)   
 [タスク リファレンス](../msbuild/msbuild-task-reference.md)