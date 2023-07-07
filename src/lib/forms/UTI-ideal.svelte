<script lang="ts">
    import Repeatable from "../Repeatable.svelte";
    export let loading;
    
</script>

<mb-form>
    
    <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
    <mb-date time path="imip-uti-tx.v8/context/document_entry_metadata/document_creation_time" label="Data"></mb-date>
    <mb-context path="imip-uti-tx.v8/context/start_time"></mb-context>
    <mb-context path="imip-uti-tx.v8/context/setting"></mb-context> 
    

    <p class="font-bold text-lg">Alergias</p>
    <Repeatable let:i>
        <mb-input path="imip-uti-tx.v8/adverse_reaction_risk:{i}/substance" label="Substância"></mb-input>
        <mb-context path="imip-uti-tx.v8/adverse_reaction_risk:{i}/language"></mb-context>
        <mb-context path="imip-uti-tx.v8/adverse_reaction_risk:{i}/encoding"></mb-context>
        <mb-context path="imip-uti-tx.v8/adverse_reaction_risk:{i}/subject"></mb-context>
    </Repeatable>
    <mb-quantity default="kg" path="imip-uti-tx.v8/body_weight/weight" label="Peso">
        <mb-unit unit="kg" label="kg" min="" max="1000"></mb-unit>
    </mb-quantity>
    <mb-context path="imip-uti-tx.v8/body_weight/time"></mb-context>
    <mb-context path="imip-uti-tx.v8/body_weight/language"></mb-context>
    <mb-context path="imip-uti-tx.v8/body_weight/encoding"></mb-context>
    <mb-context path="imip-uti-tx.v8/body_weight/subject"></mb-context>
    
    </div>
    
    <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
    <p class="font-bold text-lg">Hipoteses diagnosticas</p>
    <Repeatable let:i>

        <mb-input path="imip-uti-tx.v8/problem_diagnosis:{i}/problem_diagnosis_name" label="#{i+1}"></mb-input>
        <mb-context path="imip-uti-tx.v8/problem_diagnosis:{i}/language"></mb-context>
        <mb-context path="imip-uti-tx.v8/problem_diagnosis:{i}/encoding"></mb-context>
        <mb-context path="imip-uti-tx.v8/problem_diagnosis:{i}/subject"></mb-context>
    </Repeatable>
    </div>
    
    <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
        <p class="font-bold text-lg">Dispositivos</p>
        <Repeatable let:i>
            <div class="border shadow-md rounded-lg flex flex-row gap-3 p-4">
                <mb-input path="imip-uti-tx.v8/physical_examination_findings/any_event:0/medical_device:{i}/device_name" label="Dispositivo"></mb-input>
                <mb-input path="imip-uti-tx.v8/physical_examination_findings/any_event:0/medical_device:{i}/anatomical_location/body_site_name" label="Local"></mb-input>
                <mb-date time path="imip-uti-tx.v8/physical_examination_findings/any_event:0/medical_device:{i}/date_of_insertion" label="Data de inserção"></mb-date>
            </div>
        </Repeatable>
        </div>

        <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
            <p class="font-bold text-lg">Drogas em BIC</p>
            <Repeatable let:i>
                <div class="border shadow-md rounded-lg flex flex-row gap-3 p-4">
                    <mb-input path="imip-uti-tx.v8/physical_examination_findings/any_event:0/continuous_infusion_medications:{i}/name" label="Droga"></mb-input>
                    <mb-input  path="imip-uti-tx.v8/physical_examination_findings/any_event:0/continuous_infusion_medications:{i}/amount" label="Dose"></mb-input>
                    <mb-text-select path="imip-uti-tx.v8/physical_examination_findings/any_event:0/continuous_infusion_medications:{i}/amount_unit" label="Unidade">
                        <mb-option value="g/dia" label="g/dia"></mb-option>
                        <mb-option value="mg/kg/dia" label="mg/kg/dia"></mb-option>
                        <mb-option value="mL/h" label="mL/h"></mb-option>
                    </mb-text-select>
                </div>
            </Repeatable>
        </div>

        <mb-context path="imip-uti-tx.v8/physical_examination_findings/any_event:0/time"></mb-context>  
        <mb-context path="imip-uti-tx.v8/physical_examination_findings/language"></mb-context>
        <mb-context path="imip-uti-tx.v8/physical_examination_findings/encoding"></mb-context>
        <mb-context path="imip-uti-tx.v8/physical_examination_findings/subject"></mb-context>


        <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
            <p class="font-bold text-lg">Antibioticoterapia</p>
            <Repeatable let:i>
                <div class="border shadow-md rounded-lg flex flex-row gap-3 p-4">
                    <mb-input path="imip-uti-tx.v8/medication_statement/any_event:{i}/medication_item_name" label="Antibiótico"></mb-input>
                    <mb-date time path="imip-uti-tx.v8/medication_statement/any_event:{i}/first_prescribed" label="Início"></mb-date>
                    <mb-date time path="imip-uti-tx.v8/medication_statement/any_event:{i}/discontinued" label="Término"></mb-date>
                    <mb-context path="imip-uti-tx.v8/medication_statement/any_event:{i}/time"></mb-context>
                    <mb-context path="imip-uti-tx.v8/medication_statement/language"></mb-context>
                    <mb-context path="imip-uti-tx.v8/medication_statement/encoding"></mb-context>
                    <mb-context path="imip-uti-tx.v8/medication_statement/subject"></mb-context>
                </div>
            </Repeatable>
        </div>

        <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
            <p class="font-bold text-lg">Dados de enfermagem</p>
            <div class="border shadow-md rounded-lg flex flex-col gap-3 p-4">
                <p class="font-bold text-sm">Saídas</p>
                <Repeatable let:i> 
                <div class="flex flex-row gap-3">
                      
                    <mb-input path="imip-uti-tx.v8/fluid_output:{i}/any_event:0/fluid_name" label="Fluido/origem"></mb-input>
                    <mb-quantity default="ml" path="imip-uti-tx.v8/fluid_output:{i}/any_event:0/volume" label="Volume">
                                    <mb-unit unit="ml" label="ml" min="" max=""></mb-unit>
                    <mb-unit unit="l" label="l" min="" max=""></mb-unit>
                                </mb-quantity>
                    <mb-context path="imip-uti-tx.v8/fluid_output:{i}/any_event:0/width"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_output:{i}/any_event:0/math_function"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_output:{i}/any_event:0/time"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_output:{i}/language"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_output:{i}/encoding"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_output:{i}/subject"></mb-context>
                    </Repeatable>
            

                    <mb-quantity default="ml" path="imip-uti-tx.v8/fluid_balance/any_interval_event:0/fluid_balance" label="Balanço hídrico">
                        <mb-unit unit="ml" label="ml" min="" max=""></mb-unit>
                        <mb-unit unit="l" label="l" min="" max=""></mb-unit>
                    </mb-quantity>
                    <mb-context path="imip-uti-tx.v8/fluid_balance/any_interval_event:0/width"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_balance/any_interval_event:0/math_function"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_balance/any_interval_event:0/time"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_balance/language"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_balance/encoding"></mb-context>
                    <mb-context path="imip-uti-tx.v8/fluid_balance/subject"></mb-context>
                    
                    <div class="flex flex-row gap-3">
                        <mb-buttons path="imip-uti-tx.v8/body_temperature/any_event:0/comment" label="Distermias">
                            <mb-option value="Sim" label="Sim"></mb-option>
                            <mb-option value="Não" label="Não"></mb-option>
                        </mb-buttons>
                    <mb-quantity default="Cel" path="imip-uti-tx.v8/body_temperature/any_event:0/temperature" label="T max">
                        <mb-unit unit="Cel" label="Cel" min="" max="100"></mb-unit>
                    </mb-quantity>
                    
                    <mb-context path="imip-uti-tx.v8/body_temperature/any_event:0/width"></mb-context>
                    <mb-context path="imip-uti-tx.v8/body_temperature/any_event:0/math_function"></mb-context>
                    <mb-context path="imip-uti-tx.v8/body_temperature/any_event:0/time"></mb-context>
                    <mb-context path="imip-uti-tx.v8/body_temperature/language"></mb-context>
                    <mb-context path="imip-uti-tx.v8/body_temperature/encoding"></mb-context>
                    <mb-context path="imip-uti-tx.v8/body_temperature/subject"></mb-context>
                    </div>

                    <div class="flex flex-row place-content-between">
                        <mb-buttons path="imip-uti-tx.v8/faecal_output/any_event:0/comment" label="Evacuações">
                            <mb-option value="Ausente" label="Ausente"></mb-option>
                            <mb-option value="Normal" label="Normal"></mb-option>
                            <mb-option value="Diarréia" label="Diarréia"></mb-option>
                            <mb-option value="Melena" label="Melena"></mb-option>
                          </mb-buttons>
                        <mb-context path="imip-uti-tx.v8/faecal_output/any_event:0/width"></mb-context>
                        <mb-context path="imip-uti-tx.v8/faecal_output/any_event:0/math_function"></mb-context>
                        <mb-context path="imip-uti-tx.v8/faecal_output/any_event:0/time"></mb-context>
                        <mb-context path="imip-uti-tx.v8/faecal_output/language"></mb-context>
                        <mb-context path="imip-uti-tx.v8/faecal_output/encoding"></mb-context>
                        <mb-context path="imip-uti-tx.v8/faecal_output/subject"></mb-context>
                    </div>
                    
                    
                    
                    <mb-buttons path="imip-uti-tx.v8/laboratory_test_result/any_event:0/conclusion" label="Glicemia">
                        <mb-option value="Normal" label="Normal"></mb-option>
                        <mb-option value="Hiperglicemia" label="Hiperglicemia"></mb-option>
                        <mb-option value="Hipoglicemia" label="Hipoglicemia"></mb-option>
                    </mb-buttons>
                    <mb-context type="hidden" path="imip-uti-tx.v8/laboratory_test_result/any_event:0/test_name" value="glicemia"></mb-context>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/any_event:0/laboratory_analyte_result:0/analyte_name" value="glicemia"></mb-context>
                    <mb-quantity default="mg/dL" path="imip-uti-tx.v8/laboratory_test_result/any_event:0/laboratory_analyte_result:0/analyte_result:0" label="Glicemias">
                        <mb-unit unit="mg/dL" label="mg/dL" min="" max="1000"></mb-unit>   
                                </mb-quantity>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/any_event:0/width"></mb-context>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/any_event:0/math_function"></mb-context>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/any_event:0/time"></mb-context>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/language"></mb-context>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/encoding"></mb-context>
                    <mb-context path="imip-uti-tx.v8/laboratory_test_result/subject"></mb-context>
                

                    
            </div>
        </div>

        <div class="border shadow-lg p-5 rounded-lg flex flex-col gap-3 mt-5 md:p-10">
            <p class="font-bold text-lg">Condutas</p>
            <Repeatable let:i> 
            <mb-input path="imip-uti-tx.v8/care_plan_request:{i}/activity/plan_name" label="#{i+1}"></mb-input>
            <mb-context path="imip-uti-tx.v8/care_plan_request:{i}/activity/timing"></mb-context>
            <mb-context path="imip-uti-tx.v8/care_plan_request:{i}/narrative"></mb-context>
            <mb-context path="imip-uti-tx.v8/care_plan_request:{i}/language"></mb-context>
            <mb-context path="imip-uti-tx.v8/care_plan_request:{i}/encoding"></mb-context>
            <mb-context path="imip-uti-tx.v8/care_plan_request:{i}/subject"></mb-context>
            </Repeatable>
        </div>
        
        <mb-context path="imip-uti-tx.v8/category"></mb-context>
        <mb-context path="imip-uti-tx.v8/language"></mb-context>
        <mb-context path="imip-uti-tx.v8/territory"></mb-context>
        <mb-context path="imip-uti-tx.v8/composer"></mb-context>

    <mb-submit class="mt-4">
        <sl-button size="medium" class="mt-4 w-full" type="neutral" {loading}>
            Submit
        </sl-button>
    </mb-submit>
</mb-form>

